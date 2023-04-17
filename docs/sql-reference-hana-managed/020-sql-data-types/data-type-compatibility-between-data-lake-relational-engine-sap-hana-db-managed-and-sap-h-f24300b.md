<!-- loiof24300b848f8407d9a1ba3ca1035bc06 -->

# Data Type Compatibility Between Data Lake Relational Engine \(SAP HANA DB-Managed\) and SAP HANA Database

How you create the data lake Relational Engine table determines the compatibility of data types between SAP HANA database and data lake Relational Engine \(SAP HANA DB-Managed\)



In data lake Relational Engine \(SAP HANA DB-Managed\), when you create a physical data lake Relational Engine table, a corresponding SAP HANA database virtual table pointing to the physical data lake Relational Engine table is automatically created. The syntax used to create the physical table determines which engine \(data lake Relational Engine or SAP HANA database\) is used to map and convert \(when necessary\) the data types in the corresponding virtual table.


<table>
<tr>
<th valign="top">

Statement Name



</th>
<th valign="top">

See



</th>
</tr>
<tr>
<td valign="top">

CREATE TABLE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)



</td>
<td valign="top">

[Data Types Compatibility with SAP HANA Database for the CREATE TABLE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/data-types-compatibility-with-sap-hana-database-for-the-create-table-statement-for-data-l-e77d888.md)



</td>
</tr>
<tr>
<td valign="top">

CREATE VIRTUAL TABLE Statement for SAP HANA Database



</td>
<td valign="top">

[Data Type Compatibility with Data Lake Relational Engine for CREATE VIRTUAL TABLE Statement in SAP HANA Database](../080-sap-hana-database-for-data-lake-relational-engine/data-type-compatibility-with-data-lake-relational-engine-fo-fba2b34.md)



</td>
</tr>
<tr>
<td valign="top">

CREATE EXISTING TABLE Statement for Data Lake Relational Engine



</td>
<td valign="top">

[Data Types Compatibility with SAP HANA Database for CREATE EXISTING TABLE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/data-types-compatibility-with-sap-hana-database-for-create-existing-table-statement-for-d-dc89a0d.md)



</td>
</tr>
</table>

