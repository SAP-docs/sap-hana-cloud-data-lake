<!-- loioa5bc6ce984f21015a5b1fbca46ba89ce -->

# sp\_iqunusedindex System Procedure for Data Lake Relational Engine

Reports secondary \(non-FP\) indexes that were not referenced by the workload.



<a name="loioa5bc6ce984f21015a5b1fbca46ba89ce__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqunusedindex 
```



<a name="loioa5bc6ce984f21015a5b1fbca46ba89ce__section_wnm_sxc_yyb"/>

## Parameters

None.



<a name="loioa5bc6ce984f21015a5b1fbca46ba89ce__section_mhb_l4m_nbb"/>

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

IndexName

</td>
<td valign="top">

Index name

</td>
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

Owner

</td>
<td valign="top">

User name of index owner

</td>
</tr>
<tr>
<td valign="top">

IndexType

</td>
<td valign="top">

Index type

</td>
</tr>
</table>



<a name="loioa5bc6ce984f21015a5b1fbca46ba89ce__iq_refbb_1827"/>

## Remarks

Indexes from tables created in SYSTEM or local temporary tables are not reported.



<a name="loioa5bc6ce984f21015a5b1fbca46ba89ce__iq_refbb_1826"/>

## Privileges

Requires all of the following:

-   EXECUTE object-level privilege on this procedure
-   MONITOR system privilege



## Side Effects

None.



<a name="loioa5bc6ce984f21015a5b1fbca46ba89ce__iq_refbb_1829"/>

## Examples

This example returns a list of the non-FP indexes that are not referenced by the workload.

```
CALL sp_iqunusedindex;
```


<table>
<tr>
<th valign="top">

IndexName

</th>
<th valign="top">

TableName

</th>
<th valign="top">

Owner

</th>
<th valign="top">

IndexType

</th>
</tr>
<tr>
<td valign="top">

ASIQ\_IDX\_T450\_I7\_HG

</td>
<td valign="top">

SalesOrders

</td>
<td valign="top">

HDLADMIN

</td>
<td valign="top">

HG

</td>
</tr>
<tr>
<td valign="top">

ASIQ\_IDX\_T450\_C6\_HG

</td>
<td valign="top">

SalesOrders

</td>
<td valign="top">

HDLADMIN

</td>
<td valign="top">

HG

</td>
</tr>
<tr>
<td valign="top">

ASIQ\_IDX\_T450\_C4\_HG

</td>
<td valign="top">

SalesOrders

</td>
<td valign="top">

HDLADMIN

</td>
<td valign="top">

HG

</td>
</tr>
<tr>
<td valign="top">

ASIQ\_IDX\_T453\_I10\_HG

</td>
<td valign="top">

Contacts

</td>
<td valign="top">

HDLADMIN

</td>
<td valign="top">

HG

</td>
</tr>
<tr>
<td valign="top">

ASIQ\_IDX\_T454\_I4\_HG

</td>
<td valign="top">

FinancialCodes

</td>
<td valign="top">

HDLADMIN

</td>
<td valign="top">

HG

</td>
</tr>
<tr>
<td valign="top">

ASIQ\_IDX\_T455\_I5\_HG

</td>
<td valign="top">

FinancialData

</td>
<td valign="top">

HDLADMIN

</td>
<td valign="top">

HG

</td>
</tr>
<tr>
<td valign="top">

ASIQ\_IDX\_T455\_C3\_HG

</td>
<td valign="top">

FinancialData

</td>
<td valign="top">

HDLADMIN

</td>
<td valign="top">

HG

</td>
</tr>
</table>

**Related Information**  


[sp\_iqcolumnuse System Procedure for Data Lake Relational Engine](sp-iqcolumnuse-system-procedure-for-data-lake-relational-engine-a59fb88.md "Reports detailed usage information for columns accessed by the workload.")

[sp\_iqindexadvice System Procedure for Data Lake Relational Engine](sp-iqindexadvice-system-procedure-for-data-lake-relational-engine-a5ab8bc.md "Displays stored index advice messages. Optionally clears advice storage.")

[sp\_iqindexuse System Procedure for Data Lake Relational Engine](sp-iqindexuse-system-procedure-for-data-lake-relational-engine-a5ae206.md "Reports detailed usage information for secondary (non-FP) indexes accessed by the workload.")

[sp\_iqtableuse System Procedure for Data Lake Relational Engine](sp-iqtableuse-system-procedure-for-data-lake-relational-engine-a5bae03.md "Reports detailed usage information for tables accessed by the workload.")

[sp\_iqunusedcolumn System Procedure for Data Lake Relational Engine](sp-iqunusedcolumn-system-procedure-for-data-lake-relational-engine-a5bbef3.md "Reports columns that were not referenced by the workload.")

[sp\_iqunusedtable System Procedure for Data Lake Relational Engine](sp-iqunusedtable-system-procedure-for-data-lake-relational-engine-a5bced3.md "Reports tables that were not referenced by the workload.")

[sp\_iqworkmon System Procedure for Data Lake Relational Engine](sp-iqworkmon-system-procedure-for-data-lake-relational-engine-a5c13d2.md "Controls collection of workload monitor usage information, and reports monitoring collection status. sp_iqworkmon collects information only for queries (SQL statements containing a FROM clause). You cannot use sp_iqworkmon for INSERT or LOAD statements.")

