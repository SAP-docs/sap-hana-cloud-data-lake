<!-- loioa3e7af2384f21015a1f8b6d3c8794f47 -->

# REVOKE Object-Level Privilege Statement for Data Lake Relational Engine

Removes object-level privileges that were given using the `GRANT` statement.



<a name="loioa3e7af2384f21015a1f8b6d3c8794f47__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
REVOKE { <object-level-privilege> [,...]
   ON { [ <owner>.]<object-name> 
      | SCHEMA <schema-name> } 
   FROM <user_role_shema> [,...]
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa3e7af2384f21015a1f8b6d3c8794f47__revoke_object_priv_parm1"/>

## Parameters


<dl>
<dt><b>

*<user\_role\_schema\>*

</b></dt>
<dd>

Must be the name of existing users, immutable roles, or schemas. Separate the list with commas.



</dd><dt><b>

*<object-level-privilege\>*

</b></dt>
<dd>

Specifies the object or schema privilege being revoked.

```
<object-level-privilege> ::=
   ALL [ PRIVILEGES ] 
   | ALTER 
   | BACKUP TABLE
   | CREATE ANY
   | DELETE 
   | DROP
   | EXECUTE
   | EXECUTE PROCEDURE
   | INSERT
   | LOAD
   | REFERENCES [ ( <column-name> [, …] ) ] 
   | RESTORE TABLE
   | SELECT [ ( <column-name> [, …] ) ] 
   | TRUNCATE
   | UPDATE [ ( <column-name>, …) ]
   | USAGE
```

For an explanation of each object-level privilege, see [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md).



</dd><dt><b>

*<object-name\>*

</b></dt>
<dd>

Specifies the type of object the privilege applies to.

```
<object-name> ::=
   <table_name>
   | <view_name>
   | { <procedure-name> | <user-defined-function-name> }
   | <sequence_name>
```



</dd>
</dl>



<a name="loioa3e7af2384f21015a1f8b6d3c8794f47__revoke_privileges1"/>

## Privileges



### 

To revoke the BACKUP TABLE object-level privilege requires one of:

-   BACKUP OWNER TABLE or BACKUP ANY TABLE system privilege if you own the table.
-   BACKUP ANY TABLE system privilege granted with the WITH ADMIN option if the table is owned by another user.
-   BACKUP TABLE object-level privilege granted with the WITH GRANT option on the table being backed up regardless of ownership.

To revoke the RESTORE TABLE object-level privilege requires one of:

-   RESTORE OWNER TABLE or RESTORE ANY TABLE system privilege if you own the table.
-   RESTORE ANY TABLE system privilege if the table is owned by another user.
-   RESTORE TABLE object-level privilege granted with the WITH GRANT option on the table being restored regardless of ownership.

To revoke any other object-level privilege requires one of:

-   You own the object.
-   You have the MANAGE ANY OBJECT PRIVILEGE system privilege.
-   You have been granted the specific object-level privilege with the WITH GRANT OPTION clause on the object if the object is owned by another user.
-   You have been granted the specific object-level privilege with the WITH GRANT OPTION clause on the schema containing the object if the schema is owned by another user.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) or [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md) for assistance with granting privileges.



<a name="loioa3e7af2384f21015a1f8b6d3c8794f47__revoke_object_priv_standards1"/>

## Standards

-   SQL – syntax is an entry-level feature.
-   SAP database products – supported by SAP Adaptive Server Enterprise



<a name="loioa3e7af2384f21015a1f8b6d3c8794f47__revoke_object_priv_examples1"/>

## Examples

This example prevents user1 from inserting into the table Employees:

```
REVOKE INSERT ON Employees FROM user1;
```

This example prevents user1 from updating any objects in schema myschema1:

```
REVOKE UPDATE ON SCHEMA myschema1 FROM user1;
```

**Related Information**  


[GRANT Object-Level Privilege Statement for Data Lake Relational Engine](grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md "Grants database object-level privileges on individual objects and schemas to a user or role.")

[REVOKE Object-Level Privilege Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/f14139fa124d4e5da23c1da6a5009417.html "Removes object-level privileges that were given using the GRANT statement.") :arrow_upper_right:

