<!-- loioa3e7af2384f21015a1f8b6d3c8794f47 -->

# REVOKE Object-Level Privilege Statement for Data Lake Relational Engine

Removes object-level privileges that were given using the `GRANT` statement.



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
REVOKE { <object-level-privilege> [,...]
   ON { [ <owner>.]<object-name> | SCHEMA <schema-name> } 
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
   | CREATE ANY**
   | DELETE 
   | DROP**
   | EXECUTE
   | EXECUTE PROCEDURE**
   | INSERT
   | LOAD
   | REFERENCES [ ( <column-name> [, …] ) ] 
   | RESTORE TABLE
   | SELECT [ ( <column-name> [, …] ) ] 
   | TRUNCATE
   | UPDATE [ ( <column-name>, …) ]
   | USAGE*

**CREATE ANY, DROP, and EXECUTE PROCEDURE are only supported by SCHEMA <schema-name>
*USAGE is only supported by [ <owner>.]<object-name>
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
   | {<procedure-name> | <user-defined-function-name>}
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
-   BACKUP OWNER TABLE system privilege plus BACKUP TABLE object-level privilege granted with the WITH GRANT option on the schema that contains the table being backed up if the schema is owned by another user.

To revoke the RESTORE TABLE object-level privilege requires one of:

-   RESTORE OWNER TABLE or RESTORE ANY TABLE system privilege if you own the table.
-   RESTORE ANY TABLE system privilege if the table is owned by another user.
-   RESTORE TABLE object-level privilege granted with the WITH GRANT option on the table being restored regardless of ownership.
-   RESTORE OWNER TABLE system privilege plus RESTORE TABLE object-level privilege granted with the WITH GRANT option on the schema to contain the table being restored if the schema is owned by another user.

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

-   The following example prevents user `Dave` from inserting into the `Employees` table:

    ```
    REVOKE INSERT ON Employees FROM Dave
    ```

-   The following example prevents user `Dave` from updating the `Employees` table:

    ```
    REVOKE UPDATE ON Employees FROM Dave
    ```


**Related Information**  


[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[REVOKE Object-Level Privilege Statement for Data Lake Relational Engine](revoke-object-level-privilege-statement-for-data-lake-relational-engine-a3e7af2.md "Removes object-level privileges that were given using the GRANT statement.")

