<!-- loioa44c032384f21015af648b695e72aee9 -->

# sp\_has\_role Procedurefor Data Lake Relational Engine

Returns an integer value indicating whether the invoking user has been granted a specified system privilege or user-defined role. When used for privilege checking within user-defined stored procedures, sp\_has\_role returns an error message when a user fails a privilege check.



```
sp_has_role ( [ <rolename> ], [ <grant_type> ], [ <throw_error> ] )
```



## Parameters


<dl>
<dt><b>

*<rolename\>*

</b></dt>
<dd>

The name of a system privilege or user-defined role.



</dd><dt><b>

*<grant\_type\>*

</b></dt>
<dd>

Valid values are: ADMIN and NO ADMIN. If NULL or not specified, NO ADMIN is used by default.



</dd><dt><b>

*<throw\_error\>*

</b></dt>
<dd>

Valid values are:

-   1 – display error message specified if system privilege or user-defined role is not granted to invoking user.
-   0 – \(default\) do not display error message if specified system privilege or user-defined role is not granted to invoking user.



</dd>
</dl>



## Returns


<table>
<tr>
<th valign="top">

Value



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

System privilege or user-defined role is granted to invoking user.



</td>
</tr>
<tr>
<td valign="top">

0 or ***Permission denied: you do not have permission to execute this command/procedure.***



</td>
<td valign="top">

System privilege or user-defined role is not granted to invoking user. The error message replaces the value 0 when the throw\_error argument is set to 1.



</td>
</tr>
<tr>
<td valign="top">

\-1



</td>
<td valign="top">

The system privilege or user-defined role specified does not exist. No error message appears, even if the throw\_error argument is set to 1.



</td>
</tr>
</table>



## Remarks

If the value of the grant\_type argument is ADMIN, the function checks whether the invoking user has administrative privileges for the system privilege. If the value of the grant\_type argument is NO ADMIN, the function checks whether the invoking user has privileged use of the system privilege or role.

If the grant\_type argument is not specified, NO ADMIN is used by default and output indicates only whether the invoking user has been granted, either directly or indirectly, the specified system privilege or user-defined role.

If the rolename and grant\_type arguments are both NULL and the throw\_error argument is 1, you see an error message. You may find this useful for those stored procedures where an error message appears after certain values are read from the catalog tables rather than after the checking the presence of certain system privileges for the invoking user.

> ### Note:  
> A permission denied error message is returned if the arguments rolename and grant\_type are set to NULL and throw\_error is set to 1, or if all three arguments are set to NULL.



<a name="loioa44c032384f21015af648b695e72aee9__section_pg4_3kz_wxb"/>

## Privileges

None



## Examples

The examples use the following scenario:

-   u1 has been granted the CREATE ANY PROCEDURE system privilege with the WITH NO ADMIN OPTION clause.
-   u1 has not been granted the CREATE ANY TABLE system privilege.
-   u1 has been granted the user-defined role Role\_A with the WITH ADMIN ONLY OPTION clause.
-   Role\_B exists, but has not been granted to u1
-   The role Role\_C does not exist.

The sp\_has\_role examples are:

-   The following example returns the value 1, which indicates u1 has been granted the CREATE ANY PROCEDURE system privilege:

    ```
    sp_has_role 'create any procedure'
    ```

-   The following example returns the value 0, which indicates u1 has not been granted the CREATE ANY TABLE system privilege:

    ```
    sp_has_role 'create any table'
    ```

    No error message is returned because the throw\_error argument is not specified.

-   The following example returns the Permission denied error message \(throw\_error=1\):

    ```
    sp_has_role 'create any procedure','admin',1
    ```

    Even though u1 has been granted the CREATE ANY PROCEDURE system privilege, u1 has not been granted administrative rights to the system privilege.

-   The following example returns the value 1, which indicates u1 has been granted role Role\_A:

    ```
    sp_has_role 'Role_A'
    ```

-   The following example returns the value 1, which indicates u1 has been granted role Role\_A with administrative rights:

    ```
    sp_has_role 'Role_A','admin',1
    ```

-   The following example returns the value 0, which indicates u1 has not been granted the role ROLE\_B:

    ```
    sp_has_role 'Role_B'
    ```

    No error message is returned because the throw\_error argument is not specified.

-   The following example returns the value -1, which indicates the role ROLE\_C does not exist:

    ```
    sp_has_role 'Role_C'
    ```

-   The following example returns the value -1, which indicates the role ROLE\_C does not exist:

    ```
    sp_has_role 'Role_C',NULL,1
    ```


