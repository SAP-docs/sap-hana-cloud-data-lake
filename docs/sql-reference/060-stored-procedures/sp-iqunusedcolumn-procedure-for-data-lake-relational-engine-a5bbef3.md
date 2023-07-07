<!-- loioa5bbef3f84f21015937df763d796616f -->

# sp\_iqunusedcolumn Procedure for Data Lake Relational Engine

Reports IQ columns that were not referenced by the workload.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqunusedcolumn
```



<a name="loioa5bbef3f84f21015937df763d796616f__section_dbs_rrm_nbb"/>

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

Requires EXECUTE object-level privilege on the procedure, along with the MONITOR system privilege.



## Side Effects

None



<a name="loioa5bbef3f84f21015937df763d796616f__iq_refbb_1824"/>

## Example

The following shows sample output from sp\_iqunusedcolumn:

```
TableName        ColumnName           Owner SalesOrders        ID           GROUPO
SalesOrders      CustomerID           GROUPO SalesOrders       OrderDate    GROUPO
SalesOrders      FinancialCode        GROUPO SalesOrders       Region       GROUPO
SalesOrders      SalesRepresentative  GROUPO SalesOrderItems   ID           GROUPO
SalesOrderItems  LineID               GROUPO SalesOrderItems   ProductID    GROUPO
SalesOrderItems  Quantity             GROUPO SalesOrderItems   ShipDate     GROUPO
Contacts         ID                   GROUPO Contacts          Surname      GROUPO
Contacts         GivenName            GROUPO ...
```

**Related Information**  


[sp\_iqcolumnuse Procedure for Data Lake Relational Engine](sp-iqcolumnuse-procedure-for-data-lake-relational-engine-a59fb88.md "Reports detailed usage information for columns accessed by the workload.")

[sp\_iqindexadvice Procedure for Data Lake Relational Engine](sp-iqindexadvice-procedure-for-data-lake-relational-engine-a5ab8bc.md "Displays stored index advice messages. Optionally clears advice storage.")

[sp\_iqindexuse Procedure for Data Lake Relational Engine](sp-iqindexuse-procedure-for-data-lake-relational-engine-a5ae206.md "Reports detailed usage information for secondary (non-FP) indexes accessed by the workload.")

[sp\_iqtableuse Procedure for Data Lake Relational Engine](sp-iqtableuse-procedure-for-data-lake-relational-engine-a5bae03.md "Reports detailed usage information for tables accessed by the workload.")

[sp\_iqunusedindex Procedure for Data Lake Relational Engine](sp-iqunusedindex-procedure-for-data-lake-relational-engine-a5bc6ce.md "Reports IQ secondary (non-FP) indexes that were not referenced by the workload.")

[sp\_iqunusedtable Procedure for Data Lake Relational Engine](sp-iqunusedtable-procedure-for-data-lake-relational-engine-a5bced3.md "Reports IQ tables that were not referenced by the workload.")

[sp\_iqworkmon Procedure for Data Lake Relational Engine](sp-iqworkmon-procedure-for-data-lake-relational-engine-a5c13d2.md "Controls collection of workload monitor usage information, and reports monitoring collection status. sp_iqworkmon collects information only for queries (SQL statements containing a FROM clause). You cannot use sp_iqworkmon for INSERT or LOAD statements.")

