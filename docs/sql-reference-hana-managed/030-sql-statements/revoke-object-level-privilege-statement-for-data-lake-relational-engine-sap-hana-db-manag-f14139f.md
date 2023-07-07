<!-- loiof14139fa124d4e5da23c1da6a5009417 -->

# REVOKE Object-Level Privilege Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Removes object-level privileges that were given using the `GRANT` statement.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Executing SQL Statements](remote-execute-usage-examples-for-executing-sql-statements-fd99ac0.md).
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
REVOKE { <object-level-privilege> [,...]
   ON { [ <owner>.]<object-name> | SCHEMA <schema-name> } 
   FROM <user_role_shema> [,...]
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loiof14139fa124d4e5da23c1da6a5009417__section_lzj_mgl_gtb"/>

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

For an explanation of each object-level privilege, see [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a3e154f084f21015996d891a5e9d33d2.html "Grants database object-level privileges on individual objects and schemas to a user or role.") :arrow_upper_right:.



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



<a name="loiof14139fa124d4e5da23c1da6a5009417__section_qfx_n2y_wwb"/>

## Privileges



### 

The privileges required depend on your data lake Relational Engine \(SAP HANA DB-Managed\) connection method:


<dl>
<dt><b>

Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure:

</b></dt>
<dd>

Requires one of:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



</dd><dt><b>

Connected directly to data lake Relational Engine as a data lake Relational Engine user:

</b></dt>
<dd>

Requires one of:

-   You own the object.
-   You have been granted the specific object privilege with the WITH GRANT OPTION clause on the object.
-   MANAGE ANY OBJECT PRIVILEGE system privilege.



</dd>
</dl>



<a name="loiof14139fa124d4e5da23c1da6a5009417__section_mpx_ngl_gtb"/>

## Standards

-   SQL – syntax is an entry-level feature.
-   SAP database products – supported by SAP Adaptive Server Enterprise



<a name="loiof14139fa124d4e5da23c1da6a5009417__section_qhg_pgl_gtb"/>

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


[GRANT Object-Level Privilege Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](grant-object-level-privilege-statement-for-data-lake-relational-engine-sap-hana-db-manage-c71353e.md "Grants database object-level privileges on individual objects and schemas to a user or role.")

