<!-- loioa44ba32684f2101598cba97bb3b1b4d4 -->

# sp\_displayroles System Procedure for Data Lake Relational Engine

Displays all roles granted to a user-defined role or a user, or displays the entire hierarchical tree of roles.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_displayroles(
   [ <user_role_name> ], 
   [ <display_mode> ],
   [ <grant_type> ] )
```



<a name="loioa44ba32684f2101598cba97bb3b1b4d4__sp_displayroles_parm1"/>

## Parameters

 *<user\_role\_name\>*
 :   The user role name. Valid values are:

    -   A valid system privilege name or system privilege role name
    -   A valid user-defined role name
    -   A valid user name

    By default, if no argument is specified, the current login user is used.

  *<display\_mode\>*
 :   The display mode. Valid values are:

    -   EXPAND\_UP – shows all roles granted the input role or system privilege; that is the role hierarchy tree for the parent levels.
    -   EXPAND\_DOWN – shows all roles or system privileges granted to the input role or user; that is, the role hierarchy tree for the child levels.

    If no argument is specified \(default\), only the directly granted roles or system privileges appear.

  *<grant\_type\>*
 :   The grant type. Valid values are:

    -   ALL – shows all roles or system privileges granted.
    -   NO\_ADMIN – shows all roles or system privileges granted with the WITH NO ADMIN OPTION or WITH ADMIN OPTION clause.
    -   ADMIN – shows all roles or system privileges granted with the WITH ADMIN OPTION or WITH ADMIN ONLY OPTION clause.

    If no argument is specified, `ALL` is used.

 

<a name="loioa44ba32684f2101598cba97bb3b1b4d4__sp_displayroles_resultset1"/>

## Result Set


<table>
<tr>
<th valign="top">

Column Name



</th>
<th valign="top">

Data Type



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

`role_name`



</td>
<td valign="top">

CHAR\(128\)



</td>
<td valign="top">

Lists role/system privilege name.



</td>
</tr>
<tr>
<td valign="top">

`parent_role_name`



</td>
<td valign="top">

CHAR\(128\)



</td>
<td valign="top">

Lists role name of the parent.



</td>
</tr>
<tr>
<td valign="top">

`grant_type`



</td>
<td valign="top">

CHAR\(10\)



</td>
<td valign="top">

Lists grant type.



</td>
</tr>
<tr>
<td valign="top">

`role_level`



</td>
<td valign="top">

SMALLINT



</td>
<td valign="top">

For `Expand_down` mode, 1 indicates directly granted roles; 2 indicates the next hierarchy below, and so on. For `Expand_up` mode, 0 indicates the roles to which the specified role is granted; -1 indicates the next hierarchy above, and so on.



</td>
</tr>
</table>



<a name="loioa44ba32684f2101598cba97bb3b1b4d4__sp_displayroles_remarks1"/>

## Remarks

For:

-   Name = System privilege name – the results show the system privilege name instead of the system privilege role name.
-   Mode = Expand\_down – parent\_role\_name is NULL for level 1 \(directly granted roles\). If no mode is specified \(default\), role\_level is 1 and parent\_role\_name is NULL, since only directly granted roles appear.
-   Name = User name, with Mode = expand\_up – no results are returned since a user resides at the top level in any role hierarchy. Similarly, if Name = an immutable system privilege name, with Mode = Expand\_down, no results are returned because an immutable system privilege resides at the bottom level in any role hierarchy.
-   Default Mode – parent\_role\_name column is NULL and role\_level is 1.



<a name="loioa44ba32684f2101598cba97bb3b1b4d4__section_yxz_n2j_snb"/>

## Privileges

You must have EXECUTE privilege on the system procedure.

To return the system privileges or roles for another user ID or a role, you must also have the MANAGE ROLES system privilege.



<a name="loioa44ba32684f2101598cba97bb3b1b4d4__sp_displayroles_sideefects1"/>

## Side Effects

None



<a name="loioa44ba32684f2101598cba97bb3b1b4d4__sp_displayroles_examples"/>

## Examples

These examples assume that the following GRANT statements have been executed:

```

GRANT MONITOR TO r2;GRANT CHECKPOINT TO r1;
GRANT ROLE r2 TO r1 WITH ADMIN OPTION;
GRANT ROLE r3 TO r2 WITH NO ADMIN OPTION;
GRANT ROLE r4 TO r3 WITH ADMIN ONLY OPTION;
GRANT ROLE r1 TO user1;
GRANT ROLE r1 TO r7;
GRANT ROLE r7 TO user2 WITH ADMIN OPTION;
```

-   In the following example, `sp_displayroles( 'user2', 'expand_down', 'ALL' )` produces output similar to:


    <table>
    <tr>
    <th valign="top">

    role\_name


    
    </th>
    <th valign="top">

    parent\_role\_name


    
    </th>
    <th valign="top">

    grant\_type


    
    </th>
    <th valign="top">

    role\_level


    
    </th>
    </tr>
    <tr>
    <td valign="top">

    r7


    
    </td>
    <td valign="top">

    NULL


    
    </td>
    <td valign="top">

    ADMIN


    
    </td>
    <td valign="top">

    1


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    PUBLIC


    
    </td>
    <td valign="top">

    NULL


    
    </td>
    <td valign="top">

    NO ADMIN


    
    </td>
    <td valign="top">

    1


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    dbo


    
    </td>
    <td valign="top">

    PUBLIC


    
    </td>
    <td valign="top">

    NO ADMIN


    
    </td>
    <td valign="top">

    2


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    r1


    
    </td>
    <td valign="top">

    r7


    
    </td>
    <td valign="top">

    NO ADMIN


    
    </td>
    <td valign="top">

    2


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    r2


    
    </td>
    <td valign="top">

    r1


    
    </td>
    <td valign="top">

    ADMIN


    
    </td>
    <td valign="top">

    3


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    CHECKPOINT


    
    </td>
    <td valign="top">

    r1


    
    </td>
    <td valign="top">

    NO ADMIN


    
    </td>
    <td valign="top">

    3


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    r3


    
    </td>
    <td valign="top">

    r2


    
    </td>
    <td valign="top">

    NO ADMIN


    
    </td>
    <td valign="top">

    4


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    MONITOR


    
    </td>
    <td valign="top">

    r2


    
    </td>
    <td valign="top">

    NO ADMIN


    
    </td>
    <td valign="top">

    4


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    r4


    
    </td>
    <td valign="top">

    r3


    
    </td>
    <td valign="top">

    ADMIN ONLY


    
    </td>
    <td valign="top">

    5


    
    </td>
    </tr>
    </table>
    
-   In the following example, `sp_displayroles( 'user2', 'expand_down', 'NO_ADMIN' )` produces output similar to:


    <table>
    <tr>
    <th valign="top">

    role\_name


    
    </th>
    <th valign="top">

    parent\_role\_name


    
    </th>
    <th valign="top">

    grant\_type


    
    </th>
    <th valign="top">

    role\_level


    
    </th>
    </tr>
    <tr>
    <td valign="top">

    r7


    
    </td>
    <td valign="top">

    NULL


    
    </td>
    <td valign="top">

    ADMIN


    
    </td>
    <td valign="top">

    1


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    PUBLIC


    
    </td>
    <td valign="top">

    NULL


    
    </td>
    <td valign="top">

    NO ADMIN


    
    </td>
    <td valign="top">

    1


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    dbo


    
    </td>
    <td valign="top">

    PUBLIC


    
    </td>
    <td valign="top">

    NO ADMIN


    
    </td>
    <td valign="top">

    2


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    r1


    
    </td>
    <td valign="top">

    r7


    
    </td>
    <td valign="top">

    NO ADMIN


    
    </td>
    <td valign="top">

    2


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    r2


    
    </td>
    <td valign="top">

    r1


    
    </td>
    <td valign="top">

    ADMIN


    
    </td>
    <td valign="top">

    3


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    CHECKPOINT


    
    </td>
    <td valign="top">

    r1


    
    </td>
    <td valign="top">

    NO ADMIN


    
    </td>
    <td valign="top">

    3


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    r3


    
    </td>
    <td valign="top">

    r2


    
    </td>
    <td valign="top">

    NO ADMIN


    
    </td>
    <td valign="top">

    4


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    MONITOR


    
    </td>
    <td valign="top">

    r2


    
    </td>
    <td valign="top">

    NO ADMIN


    
    </td>
    <td valign="top">

    4


    
    </td>
    </tr>
    </table>
    
-   In the following example, `sp_displayroles( 'r3', 'expand_up', 'NO_ADMIN' )` produces out put similar to:


    <table>
    <tr>
    <th valign="top">

    role\_name


    
    </th>
    <th valign="top">

    parent\_role\_name


    
    </th>
    <th valign="top">

    grant\_type


    
    </th>
    <th valign="top">

    role\_level


    
    </th>
    </tr>
    <tr>
    <td valign="top">

    r1


    
    </td>
    <td valign="top">

    r7


    
    </td>
    <td valign="top">

    NO ADMIN


    
    </td>
    <td valign="top">

    \-2


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    r2


    
    </td>
    <td valign="top">

    r1


    
    </td>
    <td valign="top">

    ADMIN


    
    </td>
    <td valign="top">

    \-1


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    r3


    
    </td>
    <td valign="top">

    r2


    
    </td>
    <td valign="top">

    NO ADMIN


    
    </td>
    <td valign="top">

    0


    
    </td>
    </tr>
    </table>
    
-   In the following example, `sp_displayroles( 'r1', 'NO_ADMIN', 'expand_up')` produces output similar to:


    <table>
    <tr>
    <th valign="top">

    role\_name


    
    </th>
    <th valign="top">

    parent\_role\_name


    
    </th>
    <th valign="top">

    grant\_type


    
    </th>
    <th valign="top">

    role\_level


    
    </th>
    </tr>
    <tr>
    <td valign="top">

    r1


    
    </td>
    <td valign="top">

    r7


    
    </td>
    <td valign="top">

    NO ADMIN


    
    </td>
    <td valign="top">

    0


    
    </td>
    </tr>
    </table>
    

**Related Information**  


[sp_displayroles System Procedure for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/8c15112761fa4dba8aa2d0cb3a89db92.html "Displays all roles granted to a user-defined role or a user, or displays the entire hierarchical tree of roles.") :arrow_upper_right:
