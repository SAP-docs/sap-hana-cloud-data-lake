<!-- loio2529cf1872074bdf88e87d4052d2ae6a -->

# DROP SCHEMA Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)



<a name="loio2529cf1872074bdf88e87d4052d2ae6a__section_kyf_nhw_ysb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:

-   Connected directly to data lake Relational Engine **coordinator** as a data lake Relational Engine user. This syntax cannot be run using the REMOTE\_EXECUTE procedure.



```
DROP SCHEMA <schema_name> [ RESTRICT ]
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio2529cf1872074bdf88e87d4052d2ae6a__section_hkm_hdl_dzb"/>

## Parameters


<dl>
<dt><b>

RESTRICT

</b></dt>
<dd>

RESTRICT drops the schema, but only when there are no objects in it. If there are still objects in the schema, then an error is returned.



</dd>
</dl>



<a name="loio2529cf1872074bdf88e87d4052d2ae6a__section_hng_3dl_dzb"/>

## Remarks

If you drop a schema, then any schema synonym that references it is also dropped. You cannot drop a user if they own a schema.



<a name="loio2529cf1872074bdf88e87d4052d2ae6a__section_r2y_3dl_dzb"/>

## Privileges



### 

-   Requires one of:

    -   You own the schema.
    -   DROP ANY DATABASE system privilege
    -   DROP ANY OBJECT system privilege


See [GRANT System Privilege Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/a3dfcb0284f21015b74ac3cded42ee69.html "Grants specific system privileges to users or roles, with or without administrative rights.") :arrow_upper_right: or [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/a3e154f084f21015996d891a5e9d33d2.html "Grants database object-level privileges on individual objects and schemas to a user or role.") :arrow_upper_right: for assistance with granting privileges.



<a name="loio2529cf1872074bdf88e87d4052d2ae6a__section_svy_jdl_dzb"/>

## Side Effects

-   Automatic commit. Clears the Data window in dbisql.



<a name="loio2529cf1872074bdf88e87d4052d2ae6a__section_efv_kdl_dzb"/>

## Examples

This example drops the schema myschema1. Including the RESTRICT clause ensures the schema is only dropped when it contains no objects:

```
DROP SCHEMA myschema1 RESTRICT;
```

**Related Information**  


[CREATE SCHEMA for Data Lake Relational Engine \(SAP HANA DB-Managed\)](create-schema-for-data-lake-relational-engine-sap-hana-db-managed-7988025.md "Creates a schema in the current instance.")

[DROP SCHEMA Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/0c4b7140839a4678aa4a99b88b2d57e2.html "Removes a schema from the database.") :arrow_upper_right:

