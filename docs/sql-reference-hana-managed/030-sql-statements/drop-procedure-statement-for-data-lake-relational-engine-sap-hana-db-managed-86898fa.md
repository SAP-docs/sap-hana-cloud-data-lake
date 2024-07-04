<!-- loio86898fa1ad8546c58b0dfa704077a491 -->

# DROP PROCEDURE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Removes a user-defined procedure from the database.



## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:

-   Connected to SAP HANA database as a SAP HANA database user..
-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
DROP PROCEDURE [ IF EXISTS ] [ <schema-name>.]<procedure-name>
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio86898fa1ad8546c58b0dfa704077a491__section_gz3_k5q_dzb"/>

## Parameters


<dl>
<dt><b>

IF EXISTS

</b></dt>
<dd>

Use if you do not want an error returned when the DROP statement attempts to remove a database object that does not exist.



</dd>
</dl>



<a name="loio86898fa1ad8546c58b0dfa704077a491__section_nck_l5q_dzb"/>

## Remarks

DROP PROCEDURE is prevented when the procedure is in use by another connection.



<a name="loio86898fa1ad8546c58b0dfa704077a491__section_bvk_m5q_dzb"/>

## Privileges



### 

The privileges required depend on your data lake Relational Engine \(SAP HANA DB-Managed\) connection method:


<dl>
<dt><b>

Connected to SAP HANA database as a SAP HANA database user.:

</b></dt>
<dd>

To use REMOTE\_EXECUTE requires one of the following:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the SAP HANA database REMOTE\_EXECUTE procedure associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



</dd><dt><b>

Connected directly to data lake Relational Engine **coordinator** as a data lake Relational Engine user:

</b></dt>
<dd>

-   Requires one of:
    -   You own the procedure
    -   DROP ANY PROCEDURE system privilege
    -   DROP ANY OBJECT system privilege
    -   DROP object-level privilege on the procedure
    -   DROP object-level privilege on the schema containing the procedure if the schema is owned by another user.




</dd>
</dl>

See [GRANT System Privilege Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a3dfcb0284f21015b74ac3cded42ee69.html "Grants specific system privileges to users or roles, with or without administrative rights.") :arrow_upper_right: or [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a3e154f084f21015996d891a5e9d33d2.html "Grants database object-level privileges on individual objects and schemas to a user or role.") :arrow_upper_right: for assistance with granting privileges.



<a name="loio86898fa1ad8546c58b0dfa704077a491__section_apt_n5q_dzb"/>

## Side Effects

-   Automatic commit. Clears the Data window in dbisql.



<a name="loio86898fa1ad8546c58b0dfa704077a491__section_akl_45q_dzb"/>

## Examples

This example drops a procedure called myprocedure1.

```
DROP PROCEDURE myprocedure1;
```

**Related Information**  


[ALTER PROCEDURE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](alter-procedure-statement-for-data-lake-relational-engine-sap-hana-db-managed-96adbf3.md "Replaces an existing procedure with a modified version. Include the entire modified procedure in the ALTER PROCEDURE statement, and reassign user permissions on the procedure.")

[CREATE PROCEDURE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](create-procedure-statement-for-data-lake-relational-engine-sap-hana-db-managed-d172ce3.md "Creates a new user-defined SQL procedure in the database.")

[DROP PROCEDURE Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/bf9d79062d4b43c0aaefba8222c8421d.html "Removes a user-defined procedure from the database.") :arrow_upper_right:

