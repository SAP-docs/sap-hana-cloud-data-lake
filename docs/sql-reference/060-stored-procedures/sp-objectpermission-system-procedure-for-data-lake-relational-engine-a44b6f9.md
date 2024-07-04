<!-- loioa44b6f9284f21015ab3cd665b7588080 -->

# sp\_objectpermission System Procedure for Data Lake Relational Engine

Generates a report on object privileges granted to the specified role, user name, schema, or object.



<a name="loioa44b6f9284f21015ab3cd665b7588080__section_idn_b13_b4b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_objectpermission ( 
   [ <object_name> ], 
   [ <object_owner> ], 
   [ <object_type> ] )
```



## Parameters


<dl>
<dt><b>

*<object\_name\>*

</b></dt>
<dd>

The name of an object, schema, user, or role. If not specified, object privileges of the current user are reported. Default value is NULL.



</dd><dt><b>

*<object\_owner\>*

</b></dt>
<dd>

The name of the object owner for the specified object name. The object privileges of the specified object owned by the specified object owner are displayed. This parameter must be specified to obtain the object privileges of an object owned by another user or role. Default value is NULL.



</dd><dt><b>

*<object\_type\>*

</b></dt>
<dd>

If no value is specified, privileges on all object types are returned. Default value is NULL. Valid values are:

-   FUNCTION
-   MATERIALIZED VIEW
-   PROCEDURE
-   SCHEMA
-   SEQUENCE
-   TABLE – column-level object privileges also appear.
-   USER
-   VIEW



</dd>
</dl>



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
-   If the input is an object \(table, view, procedure, function, schema, sequence, and so on\), then the procedure displays a list of all users and roles that have object-level privileges on the object.
-   If the input is a user, role, or schema, then the procedure displays a list of all object-level privileges granted to the user, role, or schema. The list includes any object-level privileges that are inherited through role grants.



## Privileges

Requires EXECUTE object-level privilege on this procedure.

Also requires one of the following:

-   You own the object.
-   MANAGE ANY OBJECT PRIVILEGE system privilege

To see object-level privileges granted on objects owned by a role or granted to a role also requires one of the following:

-   You are a role administrator on the role.
-   MANAGE ANY OBJECT PRIVILEGE system privilege



<a name="loioa44b6f9284f21015ab3cd665b7588080__section_pxs_pss_mbb"/>

## Side Effects

None.



## Examples

```
--- Setup for the following examples ---
GRANT MONITOR TO ROLE2;
GRANT CHECKPOINT TO ROLE1;
GRANT ROLE ROLE2 TO ROLE1 WITH ADMIN OPTION;
GRANT ROLE ROLE3 TO ROLE2 WITH NO ADMIN OPTION;
GRANT ROLE ROLE4 TO ROLE3 WITH ADMIN ONLY OPTION;
```

ROLE5 owns a table named TABLE1 and a procedure named test\_proc in the database.

USER5, which has administrative rights over ROLE5, grants the following privileges:

```
GRANT SELECT ON ROLE5.TABLE1 TO ROLE2 WITH GRANT OPTION;
GRANT SELECT (c1), UPDATE (c1) ON ROLE5.TABLE1 TO ROLE6 WITH GRANT OPTION;
GRANT EXECUTE ON ROLE5.test_proc TO ROLE3;
```

With administrative rights USER6 grants the following privileges on TABLE1 to ROLE3:

```
GRANT SELECT (c1), REFERENCES (c1) ON ROLE5.TABLE1 TO ROLE3;
```

This example returns the privileges granted to ROLE1:

```
CALL sp_objectpermission( 'ROLE1' );
```


<table>
<tr>
<th valign="top">

grantor

</th>
<th valign="top">

grantee

</th>
<th valign="top">

object\_

name

</th>
<th valign="top">

owner

</th>
<th valign="top">

object\_

type

</th>
<th valign="top">

grantor

</th>
<th valign="top">

grantable

</th>
<th valign="top">

column\_

name

</th>
<th valign="top">

privilege

</th>
</tr>
<tr>
<td valign="top">

USER5

</td>
<td valign="top">

ROLE2

</td>
<td valign="top">

TABLE1

</td>
<td valign="top">

ROLE5

</td>
<td valign="top">

TABLE

</td>
<td valign="top">

USER5

</td>
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

USER6

</td>
<td valign="top">

ROLE3

</td>
<td valign="top">

TABLE1

</td>
<td valign="top">

ROLE5

</td>
<td valign="top">

COLUMN

</td>
<td valign="top">

USER6

</td>
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

USER6

</td>
<td valign="top">

ROLE3

</td>
<td valign="top">

TABLE1

</td>
<td valign="top">

ROLE5

</td>
<td valign="top">

COLUMN

</td>
<td valign="top">

USER6

</td>
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

USER6

</td>
<td valign="top">

ROLE3

</td>
<td valign="top">

TABLE1

</td>
<td valign="top">

ROLE5

</td>
<td valign="top">

PROCEDURE

</td>
<td valign="top">

USER6

</td>
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

This example returns the privileges granted to ROLE5 on the table TABLE1.

```
CALL sp_objectpermission( 'TABLE1', 'ROLE5', 'table');
```


<table>
<tr>
<th valign="top">

grantor

</th>
<th valign="top">

grantee

</th>
<th valign="top">

object\_

name

</th>
<th valign="top">

owner

</th>
<th valign="top">

object\_

type

</th>
<th valign="top">

grantor

</th>
<th valign="top">

column\_

name

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

USER5

</td>
<td valign="top">

ROLE2

</td>
<td valign="top">

TABLE1

</td>
<td valign="top">

ROLE5

</td>
<td valign="top">

TABLE

</td>
<td valign="top">

USER5

</td>
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

USER5

</td>
<td valign="top">

ROLE6

</td>
<td valign="top">

TABLE1

</td>
<td valign="top">

ROLE5

</td>
<td valign="top">

COLUMN

</td>
<td valign="top">

USER5

</td>
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

USER5

</td>
<td valign="top">

ROLE6

</td>
<td valign="top">

TABLE1

</td>
<td valign="top">

ROLE5

</td>
<td valign="top">

COLUMN

</td>
<td valign="top">

USER5

</td>
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

USER6

</td>
<td valign="top">

ROLE3

</td>
<td valign="top">

TABLE1

</td>
<td valign="top">

ROLE5

</td>
<td valign="top">

COLUMN

</td>
<td valign="top">

USER6

</td>
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

USER6

</td>
<td valign="top">

ROLE3

</td>
<td valign="top">

TABLE1

</td>
<td valign="top">

ROLE5

</td>
<td valign="top">

COLUMN

</td>
<td valign="top">

USER6

</td>
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

