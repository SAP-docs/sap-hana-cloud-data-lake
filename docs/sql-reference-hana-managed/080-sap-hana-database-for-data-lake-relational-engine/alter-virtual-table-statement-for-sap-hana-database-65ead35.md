<!-- loio65ead3562a7a4fb68ad7869294ff0370 -->

# ALTER VIRTUAL TABLE Statement for SAP HANA Database

Refresh the metadata of an SAP HANA database virtual table that points to a data lake Relational Engine table.



## Syntax

```
ALTER VIRTUAL TABLE <hana_relational_container_schema_name>.<virtual_table_name> REFRESH DEFINITION
```



## Syntax Elements


<dl>
<dt><b>

REFRESH DEFINITION

</b></dt>
<dd>

Updates a virtual table to reflect metadata changes in the corresponding remote table.



</dd>
</dl>



## Description

This syntax is specific to refreshing an SAP HANA database virtual table's metadata in a data lake Relational Engine context. For additional non-data lake Relational Engine specific syntax , see the *ALTER VIRTUAL TABLE Statement \(Data Definition\)* in the *SAP HANA Cloud, SAP HANA Database SQL Reference Guide*.



<a name="loio65ead3562a7a4fb68ad7869294ff0370__section_opr_ddt_5cb"/>

## Permissions

You’ve the CREATE VIRTUAL TABLE object privilege on the SAP HANA database remote source for data lake Relational Engine.



<a name="loio65ead3562a7a4fb68ad7869294ff0370__section_ms4_4nr_vjb"/>

## Example

This statement refreshes the SAP HANA database virtual table SYSHDL\_CONTAINER1.V\_T1.

```
ALTER VIRTUAL TABLE SYSHDL_CONTAINER1.V_T1 REFRESH DEFINITION;
```

**Related Information**  


[CREATE VIRTUAL TABLE Statement for SAP HANA Database](create-virtual-table-statement-for-sap-hana-database-e60ebf8.md "Creates an SAP HANA database virtual table that points to a remote table for data lake Relational Engine.")

[DROP VIRTUAL TABLE Statement for SAP HANA Database](drop-virtual-table-statement-for-sap-hana-database-6a7fe7e.md "Removes an SAP HANA database virtual table that points to a data lake Relational Engine table from theSAP HANA database.")

[SAP HANA Cloud, SAP HANA Database SQL Reference Guide](https://help.sap.com/viewer/c1d3f60099654ecfb3fe36ac93c121bb/2021_01_QRC/en-US)

