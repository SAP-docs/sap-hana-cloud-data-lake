<!-- loio5dec9a675f274f768460402e176b8660 -->

# Data Type Compatibility Between Data Lake Relational Engine and SAP HANA Database

When accessing data between SAP HANA database from data lake Relational Engine some data types are handled differently or are incompatible. This is done using virtual or proxy tables.

Where the physical table exists determines which engine \(data lake Relational Engine or SAP HANA database\) is used to map and convert \(when necessary\) the data types in the corresponding virtual or proxy table.


<table>
<tr>
<th valign="top">

Statement Name



</th>
<th valign="top">

Physical Table Exists In...



</th>
<th valign="top">

See



</th>
</tr>
<tr>
<td valign="top">

[CREATE TABLE Statement for Data Lake Relational Engine](../080-sql-statements/create-table-statement-for-data-lake-relational-engine-a619764.md)



</td>
<td valign="top">

Data Lake Relational Engine



</td>
<td valign="top">

[Data Type Compatibility with SAP HANA Database for the CREATE TABLE Statement in Data Lake Relational Engine](../080-sql-statements/data-type-compatibility-with-sap-hana-database-for-the-create-table-statement-in-data-lak-eccbd1f.md)



</td>
</tr>
<tr>
<td valign="top">

[CREATE EXISTING TABLE Statement for Data Lake Relational Engine](../080-sql-statements/create-existing-table-statement-for-data-lake-relational-engine-a617378.md)



</td>
<td valign="top">

SAP HANA database



</td>
<td valign="top">

[Data Type Compatibility with SAP HANA Database for CREATE EXISTING TABLE Statement in Data Lake Relational Engine](../080-sql-statements/data-type-compatibility-with-sap-hana-database-for-create-existing-table-statement-in-dat-a23b640.md)



</td>
</tr>
</table>

