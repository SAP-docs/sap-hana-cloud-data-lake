<!-- loio58c58a93e1de4d409e3776c4b92790e1 -->

# DROP FUNCTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Removes a user-defined function from the database.



## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:

-   Connected to SAP HANA database as a SAP HANA database user..
-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
DROP FUNCTION [ IF EXISTS ] [ <schema-name>.]<function-name> 
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio58c58a93e1de4d409e3776c4b92790e1__section_uxw_drq_dzb"/>

## Parameters


<dl>
<dt><b>

IF EXISTS

</b></dt>
<dd>

Use if you do not want an error returned when the DROP statement attempts to remove a database object that does not exist.



</dd>
</dl>



<a name="loio58c58a93e1de4d409e3776c4b92790e1__section_wwm_2rq_dzb"/>

## Remarks

None



<a name="loio58c58a93e1de4d409e3776c4b92790e1__section_kcj_3rq_dzb"/>

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
    -   You own the procedure.
    -   DROP ANY PROCEDURE system privilege
    -   DROP ANY OBJECT system privilege
    -   DROP object-level privilege on the procedure
    -   DROP object-level privilege on the schema containing the procedure if the schema is owned by another user.




</dd>
</dl>

See [GRANT System Privilege Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/a3dfcb0284f21015b74ac3cded42ee69.html "Grants specific system privileges to users or roles, with or without administrative rights.") :arrow_upper_right: or [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/a3e154f084f21015996d891a5e9d33d2.html "Grants database object-level privileges on individual objects and schemas to a user or role.") :arrow_upper_right: for assistance with granting privileges.



<a name="loio58c58a93e1de4d409e3776c4b92790e1__section_pj3_jrq_dzb"/>

## Side Effects

-   Automatic commit. Clears the Data window in dbisql.



<a name="loio58c58a93e1de4d409e3776c4b92790e1__section_ulw_lrq_dzb"/>

## Standards

-   SQL – ISO/ANSI SQL compliant



<a name="loio58c58a93e1de4d409e3776c4b92790e1__section_bhb_krq_dzb"/>

## Examples

This example drops the user-defined function myfunction1 if it exists from the database.

```
DROP FUNCTION IF EXISTS myfunction1;
```

**Related Information**  


[CREATE FUNCTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](create-function-statement-for-data-lake-relational-engine-sap-hana-db-managed-abddfd6.md "Creates a user-defined function in the database. A function can be created for another user by specifying an owner name. Subject to permissions, a user-defined function can be used in exactly the same way as other non-aggregate functions.")

[ALTER FUNCTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](alter-function-statement-for-data-lake-relational-engine-sap-hana-db-managed-3d7a54b.md "Modifies an existing function. Include the entire modified function in the ALTER FUNCTION statement.")

[DROP FUNCTION Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/d42de2d8355a4762b5a47e810d55653f.html "Removes a user-defined function from the database.") :arrow_upper_right:

