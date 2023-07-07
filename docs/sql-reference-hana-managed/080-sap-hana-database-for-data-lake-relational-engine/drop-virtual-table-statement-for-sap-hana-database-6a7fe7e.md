<!-- loio6a7fe7ed9c6a4e12b494e08ec3f45880 -->

# DROP VIRTUAL TABLE Statement for SAP HANA Database

Removes an SAP HANA database virtual table that points to a data lake Relational Engine table from theSAP HANA database.



<a name="loio6a7fe7ed9c6a4e12b494e08ec3f45880__sql_drop_table_1sql_drop_table_syntax"/>

## Syntax

```
DROP TABLE <hana_relational_container_schema_name>.<virtual_table_name> [ <drop_option> ] [ WITH REMOTE ]
```



<a name="loio6a7fe7ed9c6a4e12b494e08ec3f45880__sql_drop_table_1sql_drop_table_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<drop\_option\>*

</b></dt>
<dd>

Specifies the drop option to use.

```
<drop_option> ::= { CASCADE | RESTRICT }
```

CASCADE drops the table and dependent objects. RESTRICT drops the table only when dependent objects do not exist. If this drop option is used and a dependent object exists, then an error is thrown.

If *<drop\_option\>* is not specified, then a non-cascaded drop is performed, which only drops the specified table. Dependent objects of the table are invalidated, but not dropped.

The invalidated objects can be re-validated when an object that has the same schema and object name is created.



</dd><dt><b>

WITH REMOTE

</b></dt>
<dd>

Drops the virtual table from the local source and the corresponding table on the remote source. This option is only supported for virtual tables.



</dd>
</dl>



<a name="loio6a7fe7ed9c6a4e12b494e08ec3f45880__sql_drop_table_1sql_drop_table_description"/>

## Description

The DROP TABLE statement removes a virtual table from the SAP HANA database.

Use of the WITH REMOTE option also requires the REMOTE TABLE ADMIN object privilege.



<a name="loio6a7fe7ed9c6a4e12b494e08ec3f45880__section_opr_ddt_5cb"/>

## Permissions

You’ve the CREATE VIRTUAL TABLE object privilege on the SAP HANA database remote source for data lake Relational Engine.



<a name="loio6a7fe7ed9c6a4e12b494e08ec3f45880__sql_drop_table_1sql_drop_table_examples"/>

## Example

This example drops the SAP HANA database virtual table V\_T1 in MY\_SCHEMA and the corresponding data lake Relational Engine table that it points to, along with all its dependent objects are dropped.

```
DROP TABLE MY_SCHEMA.V_T1 CASCADE WITH REMOTE;
```

**Related Information**  


[ALTER VIRTUAL TABLE Statement for SAP HANA Database](alter-virtual-table-statement-for-sap-hana-database-65ead35.md "Refresh the metadata of an SAP HANA database virtual table that points to a data lake Relational Engine table.")

[CREATE VIRTUAL TABLE Statement for SAP HANA Database](create-virtual-table-statement-for-sap-hana-database-e60ebf8.md "Creates an SAP HANA database virtual table that points to a remote table for data lake Relational Engine.")

[SAP HANA Cloud, SAP HANA Database SQL Reference Guide](https://help.sap.com/viewer/c1d3f60099654ecfb3fe36ac93c121bb/cloud/en-US)

