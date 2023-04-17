<!-- loioa5bced3184f2101594668a0e1dd0375a -->

# sp\_iqunusedtable Procedure for Data Lake Relational Engine

Reports IQ tables that were not referenced by the workload.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqunusedtable
```



<a name="loioa5bced3184f2101594668a0e1dd0375a__section_vxr_h4m_nbb"/>

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

Owner



</td>
<td valign="top">

User name of table owner



</td>
</tr>
</table>



<a name="loioa5bced3184f2101594668a0e1dd0375a__iq_refbb_1832"/>

## Remarks

Tables created in SYSTEM and local temporary tables are not reported.



<a name="loioa5bced3184f2101594668a0e1dd0375a__iq_refbb_1831"/>

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



<a name="loioa5bced3184f2101594668a0e1dd0375a__iq_refbb_1834"/>

## Example

The following table illustrates sample output from the sp\_iqunusedtable procedure:


<table>
<tr>
<th valign="top">

TableName



</th>
<th valign="top">

Owner



</th>
</tr>
<tr>
<td valign="top">

emp1



</td>
<td valign="top">

HDLADMIN



</td>
</tr>
<tr>
<td valign="top">

SalesOrderItems



</td>
<td valign="top">

GROUPO



</td>
</tr>
<tr>
<td valign="top">

sale



</td>
<td valign="top">

HDLADMIN



</td>
</tr>
<tr>
<td valign="top">

FinancialCodes



</td>
<td valign="top">

GROUPO



</td>
</tr>
<tr>
<td valign="top">

SalesOrders



</td>
<td valign="top">

GROUPO



</td>
</tr>
<tr>
<td valign="top">

Products



</td>
<td valign="top">

GROUP



</td>
</tr>
<tr>
<td valign="top">

Contacts



</td>
<td valign="top">

GROUPO



</td>
</tr>
<tr>
<td valign="top">

FinancialData



</td>
<td valign="top">

GROUPO



</td>
</tr>
<tr>
<td valign="top">

iq\_dummy



</td>
<td valign="top">

HDLADMIN



</td>
</tr>
<tr>
<td valign="top">

Employees



</td>
<td valign="top">

GROUPO



</td>
</tr>
<tr>
<td valign="top">

Departments



</td>
<td valign="top">

GROUPO



</td>
</tr>
<tr>
<td valign="top">

Customers



</td>
<td valign="top">

GROUPO



</td>
</tr>
</table>

**Related Information**  


[sp\_iqcolumnuse Procedure for Data Lake Relational Engine](sp-iqcolumnuse-procedure-for-data-lake-relational-engine-a59fb88.md "Reports detailed usage information for columns accessed by the workload.")

[sp\_iqindexadvice Procedure for Data Lake Relational Engine](sp-iqindexadvice-procedure-for-data-lake-relational-engine-a5ab8bc.md "Displays stored index advice messages. Optionally clears advice storage.")

[sp\_iqindexuse Procedure for Data Lake Relational Engine](sp-iqindexuse-procedure-for-data-lake-relational-engine-a5ae206.md "Reports detailed usage information for secondary (non-FP) indexes accessed by the workload.")

[sp\_iqtableuse Procedure for Data Lake Relational Engine](sp-iqtableuse-procedure-for-data-lake-relational-engine-a5bae03.md "Reports detailed usage information for tables accessed by the workload.")

[sp\_iqunusedcolumn Procedure for Data Lake Relational Engine](sp-iqunusedcolumn-procedure-for-data-lake-relational-engine-a5bbef3.md "Reports IQ columns that were not referenced by the workload.")

[sp\_iqunusedindex Procedure for Data Lake Relational Engine](sp-iqunusedindex-procedure-for-data-lake-relational-engine-a5bc6ce.md "Reports IQ secondary (non-FP) indexes that were not referenced by the workload.")

[sp\_iqworkmon Procedure for Data Lake Relational Engine](sp-iqworkmon-procedure-for-data-lake-relational-engine-a5c13d2.md "Controls collection of workload monitor usage information, and reports monitoring collection status. sp_iqworkmon collects information only for queries (SQL statements containing a FROM clause). You cannot use sp_iqworkmon for INSERT or LOAD statements.")

