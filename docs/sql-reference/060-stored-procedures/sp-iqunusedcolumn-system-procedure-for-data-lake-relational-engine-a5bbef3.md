<!-- loioa5bbef3f84f21015937df763d796616f -->

# sp\_iqunusedcolumn System Procedure for Data Lake Relational Engine

Reports columns that were not referenced by the workload.



<a name="loioa5bbef3f84f21015937df763d796616f__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqunusedcolumn
```



<a name="loioa5bbef3f84f21015937df763d796616f__section_sqr_qr3_yyb"/>

## Parameters

None.



<a name="loioa5bbef3f84f21015937df763d796616f__section_dbs_rrm_nbb"/>

## Result Set


<table>
<tr>
<th valign="top">

Column Name

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

TableName

</td>
<td valign="top">

Table name

</td>
</tr>
<tr>
<td valign="top">

ColumnName

</td>
<td valign="top">

Column name

</td>
</tr>
<tr>
<td valign="top">

Owner

</td>
<td valign="top">

User name of column owner

</td>
</tr>
</table>



<a name="loioa5bbef3f84f21015937df763d796616f__iq_refbb_1822"/>

## Remarks

Columns from tables created in SYSTEM or local temporary tables are not reported.



<a name="loioa5bbef3f84f21015937df763d796616f__iq_refbb_1821"/>

## Privileges

Requires all of the following:

-   EXECUTE object-level privilege on this procedure
-   MONITOR system privilege



## Side Effects

None.



<a name="loioa5bbef3f84f21015937df763d796616f__iq_refbb_1824"/>

## Examples

This example returns a list of the columns that are not referenced by the workload.

```
CALL sp_iqunusedcolumn;
```


<table>
<tr>
<th valign="top">

TableName

</th>
<th valign="top">

ColumnName

</th>
<th valign="top">

Owner

</th>
</tr>
<tr>
<td valign="top">

SalesOrders

</td>
<td valign="top">

CustomerID

</td>
<td valign="top">

USER1

</td>
</tr>
<tr>
<td valign="top">

SalesOrders

</td>
<td valign="top">

FinancialCode

</td>
<td valign="top">

USER1

</td>
</tr>
<tr>
<td valign="top">

SalesOrders

</td>
<td valign="top">

SalesRepresentative

</td>
<td valign="top">

USER1

</td>
</tr>
<tr>
<td valign="top">

SalesOrderItems

</td>
<td valign="top">

LineID

</td>
<td valign="top">

USER1

</td>
</tr>
<tr>
<td valign="top">

SalesOrderItems

</td>
<td valign="top">

Quantity

</td>
<td valign="top">

USER1

</td>
</tr>
<tr>
<td valign="top">

Contacts

</td>
<td valign="top">

ID

</td>
<td valign="top">

USER1

</td>
</tr>
</table>

**Related Information**  


[sp\_iqcolumnuse System Procedure for Data Lake Relational Engine](sp-iqcolumnuse-system-procedure-for-data-lake-relational-engine-a59fb88.md "Reports detailed usage information for columns accessed by the workload.")

[sp\_iqindexadvice System Procedure for Data Lake Relational Engine](sp-iqindexadvice-system-procedure-for-data-lake-relational-engine-a5ab8bc.md "Displays stored index advice messages. Optionally clears advice storage.")

[sp\_iqindexuse System Procedure for Data Lake Relational Engine](sp-iqindexuse-system-procedure-for-data-lake-relational-engine-a5ae206.md "Reports detailed usage information for secondary (non-FP) indexes accessed by the workload.")

[sp\_iqtableuse System Procedure for Data Lake Relational Engine](sp-iqtableuse-system-procedure-for-data-lake-relational-engine-a5bae03.md "Reports detailed usage information for tables accessed by the workload.")

[sp\_iqunusedindex System Procedure for Data Lake Relational Engine](sp-iqunusedindex-system-procedure-for-data-lake-relational-engine-a5bc6ce.md "Reports secondary (non-FP) indexes that were not referenced by the workload.")

[sp\_iqunusedtable System Procedure for Data Lake Relational Engine](sp-iqunusedtable-system-procedure-for-data-lake-relational-engine-a5bced3.md "Reports tables that were not referenced by the workload.")

[sp\_iqworkmon System Procedure for Data Lake Relational Engine](sp-iqworkmon-system-procedure-for-data-lake-relational-engine-a5c13d2.md "Controls collection of workload monitor usage information, and reports monitoring collection status. sp_iqworkmon collects information only for queries (SQL statements containing a FROM clause). You cannot use sp_iqworkmon for INSERT or LOAD statements.")

