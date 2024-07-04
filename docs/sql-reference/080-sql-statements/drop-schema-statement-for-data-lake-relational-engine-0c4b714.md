<!-- loio0c4b7140839a4678aa4a99b88b2d57e2 -->

# DROP SCHEMA Statement for Data Lake Relational Engine

Removes a schema from the database.



<a name="loio0c4b7140839a4678aa4a99b88b2d57e2__section_azh_5fj_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
DROP SCHEMA <schema_name> [ RESTRICT ]
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio0c4b7140839a4678aa4a99b88b2d57e2__drop_schema_param1"/>

## Parameters


<dl>
<dt><b>

RESTRICT

</b></dt>
<dd>

RESTRICT drops the schema, but only when there are no objects in it. If there are still objects in the schema, then an error is returned.



</dd>
</dl>



<a name="loio0c4b7140839a4678aa4a99b88b2d57e2__drop_schema_remarks1"/>

## Remarks

If you drop a schema, then any schema synonym that references it is also dropped. You cannot drop a user if they own a schema.



<a name="loio0c4b7140839a4678aa4a99b88b2d57e2__drop_schema_priv1"/>

## Privileges



### 

-   Requires one of:

    -   You own the schema.
    -   DROP ANY DATABASE system privilege
    -   DROP ANY OBJECT system privilege


See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) or [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md) for assistance with granting privileges.



<a name="loio0c4b7140839a4678aa4a99b88b2d57e2__drop_schema_side_effects1"/>

## Side Effects

-   Automatic commit. Clears the Data window in dbisql.



<a name="loio0c4b7140839a4678aa4a99b88b2d57e2__drop_schema_examples1"/>

## Examples

This example drops the schema myschema1. Including the RESTRICT clause ensures the schema is only dropped when it contains no objects:

```
DROP SCHEMA myschema1 RESTRICT;
```

**Related Information**  


[CREATE SCHEMA Statement for Data Lake Relational Engine](create-schema-statement-for-data-lake-relational-engine-5e20f75.md "Creates a schema in the current instance.")

[DROP SCHEMA Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/2529cf1872074bdf88e87d4052d2ae6a.html "") :arrow_upper_right:

[SET SCHEMA Statement for Data Lake Relational Engine](set-schema-statement-for-data-lake-relational-engine-b23679a.md "Sets the default schema for the connection")

