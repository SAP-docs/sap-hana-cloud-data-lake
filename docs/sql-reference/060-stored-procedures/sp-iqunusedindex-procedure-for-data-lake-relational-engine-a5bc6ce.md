<!-- loioa5bc6ce984f21015a5b1fbca46ba89ce -->

# sp\_iqunusedindex Procedure for Data Lake Relational Engine

Reports IQ secondary \(non-FP\) indexes that were not referenced by the workload.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqunusedindex 
```



<a name="loioa5bc6ce984f21015a5b1fbca46ba89ce__section_mhb_l4m_nbb"/>

## Returns


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

To run this procedure, you need the EXECUTE privilege on the procedure. See [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md). 

You also need:


<table>
<tr>
<th valign="top">

Privilege Name



</th>
<th valign="top">

Privilege Type



</th>
<th valign="top">

Grant Statement



</th>
</tr>
<tr>
<td valign="top">

MONITOR



</td>
<td valign="top">

System privilege



</td>
<td valign="top">

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md)



</td>
</tr>
</table>



## Side Effects

None



<a name="loioa5bc6ce984f21015a5b1fbca46ba89ce__iq_refbb_1829"/>

## Example

The following shows sample output from sp\_iqunusedindex:

```
IndexName            TableName             Owner  IndexType ASIQ_IDX_T450_I7_HG  SalesOrders           GROUPO HG 
ASIQ_IDX_T450_C6_HG  SalesOrders           GROUPO HG ASIQ_IDX_T450_C4_HG  SalesOrders           GROUPO HG 
ASIQ_IDX_T450_C2_HG  SalesOrders           GROUPO HG ASIQ_IDX_T451_I6_HG  SalesOrderItems       GROUPO HG 
ASIQ_IDX_T451_C3_HG  SalesOrderItems       GROUPO HG ASIQ_IDX_T451_C1_HG  SalesOrderItems       GROUPO HG 
ASIQ_IDX_T452_I11_HG Contacts              GROUPO HG ASIQ_IDX_T453_I10_HG Contacts              GROUPO HG 
ASIQ_IDX_T454_I4_HG  FinancialCodes        GROUPO HG ASIQ_IDX_T455_I5_HG  FinancialData         GROUPO HG 
ASIQ_IDX_T455_C3_HG  FinancialData         GROUPO HG ASIQ_IDX_T456_I8_HG  Products              GROUPO HG 
ASIQ_IDX_T457_I4_HG  Departments           GROUPO HG ASIQ_IDX_T457_C3_HG  Departments           GROUPO HG 
ASIQ_IDX_T458_I21_HG Departments           GROUPO HG ASIQ_IDX_T458_C5_HG  Departments           GROUPO HG
```

**Related Information**  


[sp\_iqcolumnuse Procedure for Data Lake Relational Engine](sp-iqcolumnuse-procedure-for-data-lake-relational-engine-a59fb88.md "Reports detailed usage information for columns accessed by the workload.")

[sp\_iqindexadvice Procedure for Data Lake Relational Engine](sp-iqindexadvice-procedure-for-data-lake-relational-engine-a5ab8bc.md "Displays stored index advice messages. Optionally clears advice storage.")

[sp\_iqindexuse Procedure for Data Lake Relational Engine](sp-iqindexuse-procedure-for-data-lake-relational-engine-a5ae206.md "Reports detailed usage information for secondary (non-FP) indexes accessed by the workload.")

[sp\_iqtableuse Procedure for Data Lake Relational Engine](sp-iqtableuse-procedure-for-data-lake-relational-engine-a5bae03.md "Reports detailed usage information for tables accessed by the workload.")

[sp\_iqunusedcolumn Procedure for Data Lake Relational Engine](sp-iqunusedcolumn-procedure-for-data-lake-relational-engine-a5bbef3.md "Reports IQ columns that were not referenced by the workload.")

[sp\_iqunusedtable Procedure for Data Lake Relational Engine](sp-iqunusedtable-procedure-for-data-lake-relational-engine-a5bced3.md "Reports IQ tables that were not referenced by the workload.")

[sp\_iqworkmon Procedure for Data Lake Relational Engine](sp-iqworkmon-procedure-for-data-lake-relational-engine-a5c13d2.md "Controls collection of workload monitor usage information, and reports monitoring collection status. sp_iqworkmon collects information only for queries (SQL statements containing a FROM clause). You cannot use sp_iqworkmon for INSERT or LOAD statements.")

