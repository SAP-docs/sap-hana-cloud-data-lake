<!-- loioa44b6f9284f21015ab3cd665b7588080 -->

# sp\_objectpermission System Procedure for Data Lake Relational Engine

Generates a report on object privileges granted to the specified role, user name,schema, or object.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_objectpermission ( 
   [ <object_name> ], 
   [ <object_owner> ], 
   [ <object_type> ] )
```



## Parameters

 *<object\_name\>*
 :   The name of an object,schema, user, or role. If not specified, object privileges of the current user are reported. Default value is NULL.

  *<object\_owner\>*
 :   The name of the object owner for the specified object name. The object privileges of the specified object owned by the specified object owner are displayed. This parameter must be specified to obtain the object privileges of an object owned by another user or role. Default value is NULL.

  *<object\_type\>*
 :   If no value is specified, privileges on all object types are returned. Default value is NULL. Valid values are:

    -   FUNCTION
    -   MATERIALIZED VIEW
    -   PROCEDURE
    -   SCHEMA
    -   SEQUENCE
    -   TABLE – column-level object privileges also appear.
    -   USER
    -   VIEW

 

<a name="loioa44b6f9284f21015ab3cd665b7588080__section_hfb_cpr_mbb"/>

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

grantor



</td>
<td valign="top">

CHAR\(128\)



</td>
<td valign="top">

The user ID of the grantor



</td>
</tr>
<tr>
<td valign="top">

grantee



</td>
<td valign="top">

CHAR\(128\)



</td>
<td valign="top">

The user ID of the grantee



</td>
</tr>
<tr>
<td valign="top">

object\_name



</td>
<td valign="top">

CHAR\(128\)



</td>
<td valign="top">

The name of the object



</td>
</tr>
<tr>
<td valign="top">

owner



</td>
<td valign="top">

CHAR\(128\)



</td>
<td valign="top">

The name of the object owner



</td>
</tr>
<tr>
<td valign="top">

object\_type



</td>
<td valign="top">

CHAR\(20\)



</td>
<td valign="top">

The type of object



</td>
</tr>
<tr>
<td valign="top">

column\_name



</td>
<td valign="top">

CHAR\(128\)



</td>
<td valign="top">

The name of the column



</td>
</tr>
<tr>
<td valign="top">

permission



</td>
<td valign="top">

CHAR\(20\)



</td>
<td valign="top">

The name of the privilege



</td>
</tr>
<tr>
<td valign="top">

grantable



</td>
<td valign="top">

CHAR\(1\)



</td>
<td valign="top">

Whether or not the privilege is grantable



</td>
</tr>
</table>



<a name="loioa44b6f9284f21015ab3cd665b7588080__section_wnj_bpr_mbb"/>

## Remarks

All arguments are optional and can generate these reports:

-   If the object type is not specified, then the object privileges for all existing object types matching the specified object name appear.
-   If the input is an object \(table, view, procedure, function,schema, sequence, and so on\), then the procedure displays a list of all users and roles that have object-level privileges on the object.
-   If the input is a user, role, or schema, then the procedure displays a list of all object-level privileges granted to the user, role, or schema. The list includes any object-level privileges that are inherited through role grants.



## Privileges

To run this procedure, you need the EXECUTE privilege on the procedure. See [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md). Additional privileges may be needed obtain object-level privilege information as follows:

-   To see object-level privileges granted to self-owned objects requires no additional privileges.
-   To see object-level privileges granted to other users or granted on objects owned by other users requires:
    -   MANAGE ANY OBJECT PRIVILEGE system privilege

-   To see object-level privileges that are granted on objects owned by a role or granted to a role requires one of:
    -   MANAGE ANY OBJECT PRIVILEGE system privilege
    -   You are a role administrator on the role




<a name="loioa44b6f9284f21015ab3cd665b7588080__section_pxs_pss_mbb"/>

## Side Effects

None



## Examples

The following GRANT statements are executed:

```
GRANT MONITOR TO r2;GRANT CHECKPOINT TO r1;
GRANT ROLE r2 TO r1 WITH ADMIN OPTION;
GRANT ROLE r3 TO r2 WITH NO ADMIN OPTION;
GRANT ROLE r4 TO r3 WITH ADMIN ONLY OPTION;
```

-   r5 owns a table named test\_tab and a procedure named test\_proc in the database.
-   u5, which has administrative rights over r5, grants the following privileges:

    ```
    GRANT SELECT ON r5.test_tab TO r2 WITH GRANT OPTION;
    GRANT SELECT (c1), UPDATE (c1) ON r5.test_tab TO r6 WITH GRANT OPTION;
    GRANT EXECUTE ON r5.test_proc TO r3;
    ```

-   u6, which has administrative rights over r6, grants the following privileges:

    ```
    GRANT SELECT (c1), REFERENCES (c1) ON r5.test_tab TO r3;
    ```


Executing sp\_objectpermission\( 'r1' \) produces output similar to:


<table>
<tr>
<th valign="top">

grantor



</th>
<th valign="top">

grantee



</th>
<th valign="top">

object\_name



</th>
</tr>
<tr>
<td valign="top">

u5



</td>
<td valign="top">

r2



</td>
<td valign="top">

test\_tab



</td>
</tr>
<tr>
<td valign="top">

u6



</td>
<td valign="top">

r3



</td>
<td valign="top">

test\_tab



</td>
</tr>
<tr>
<td valign="top">

u6



</td>
<td valign="top">

r3



</td>
<td valign="top">

test\_tab



</td>
</tr>
<tr>
<td valign="top">

u6



</td>
<td valign="top">

r3



</td>
<td valign="top">

test\_proc



</td>
</tr>
</table>


<table>
<tr>
<th valign="top">

\(Continued\)

owner



</th>
<th valign="top">

object\_type



</th>
<th valign="top">

grantor



</th>
</tr>
<tr>
<td valign="top">

r5



</td>
<td valign="top">

TABLE



</td>
<td valign="top">

u5



</td>
</tr>
<tr>
<td valign="top">

r5



</td>
<td valign="top">

COLUMN



</td>
<td valign="top">

u6



</td>
</tr>
<tr>
<td valign="top">

r5



</td>
<td valign="top">

COLUMN



</td>
<td valign="top">

u6



</td>
</tr>
<tr>
<td valign="top">

r5



</td>
<td valign="top">

PROCEDURE



</td>
<td valign="top">

u6



</td>
</tr>
</table>


<table>
<tr>
<th valign="top">

\(Continued\)

grantable



</th>
<th valign="top">

column\_name



</th>
<th valign="top">

privilege



</th>
</tr>
<tr>
<td valign="top">

Y



</td>
<td valign="top">

NULL



</td>
<td valign="top">

SELECT



</td>
</tr>
<tr>
<td valign="top">

N



</td>
<td valign="top">

c1



</td>
<td valign="top">

SELECT



</td>
</tr>
<tr>
<td valign="top">

Y



</td>
<td valign="top">

c1



</td>
<td valign="top">

REFERENCES



</td>
</tr>
<tr>
<td valign="top">

N



</td>
<td valign="top">

NULL



</td>
<td valign="top">

EXECUTE



</td>
</tr>
</table>

Executing sp\_objectpermission\( 'test\_tab', 'r5', 'table' \) produces output similar to:


<table>
<tr>
<th valign="top">

grantor



</th>
<th valign="top">

grantee



</th>
<th valign="top">

object\_name



</th>
</tr>
<tr>
<td valign="top">

u5



</td>
<td valign="top">

r2



</td>
<td valign="top">

test\_tab



</td>
</tr>
<tr>
<td valign="top">

u5



</td>
<td valign="top">

r6



</td>
<td valign="top">

test\_tab



</td>
</tr>
<tr>
<td valign="top">

u5



</td>
<td valign="top">

r6



</td>
<td valign="top">

test\_tab



</td>
</tr>
<tr>
<td valign="top">

u6



</td>
<td valign="top">

r3



</td>
<td valign="top">

test\_tab



</td>
</tr>
<tr>
<td valign="top">

u6



</td>
<td valign="top">

r3



</td>
<td valign="top">

test\_tab



</td>
</tr>
</table>


<table>
<tr>
<th valign="top">

\(Continued\)

owner



</th>
<th valign="top">

object\_type



</th>
<th valign="top">

grantor



</th>
</tr>
<tr>
<td valign="top">

r5



</td>
<td valign="top">

TABLE



</td>
<td valign="top">

u5



</td>
</tr>
<tr>
<td valign="top">

r5



</td>
<td valign="top">

COLUMN



</td>
<td valign="top">

u5



</td>
</tr>
<tr>
<td valign="top">

r5



</td>
<td valign="top">

COLUMN



</td>
<td valign="top">

u5



</td>
</tr>
<tr>
<td valign="top">

r5



</td>
<td valign="top">

COLUMN



</td>
<td valign="top">

u6



</td>
</tr>
<tr>
<td valign="top">

r5



</td>
<td valign="top">

COLUMN



</td>
<td valign="top">

u6



</td>
</tr>
</table>


<table>
<tr>
<th valign="top">

\(Continued\)

column\_name



</th>
<th valign="top">

privilege



</th>
<th valign="top">

grantable



</th>
</tr>
<tr>
<td valign="top">

NULL



</td>
<td valign="top">

SELECT



</td>
<td valign="top">

Y



</td>
</tr>
<tr>
<td valign="top">

c1



</td>
<td valign="top">

SELECT



</td>
<td valign="top">

Y



</td>
</tr>
<tr>
<td valign="top">

c1



</td>
<td valign="top">

UPDATE



</td>
<td valign="top">

Y



</td>
</tr>
<tr>
<td valign="top">

c1



</td>
<td valign="top">

SELECT



</td>
<td valign="top">

N



</td>
</tr>
<tr>
<td valign="top">

c1



</td>
<td valign="top">

REFERENCES



</td>
<td valign="top">

N



</td>
</tr>
</table>

