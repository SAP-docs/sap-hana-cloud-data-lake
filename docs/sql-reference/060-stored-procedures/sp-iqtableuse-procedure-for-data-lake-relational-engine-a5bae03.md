<!-- loioa5bae03284f210159da88fd013c0d1ee -->

# sp\_iqtableuse Procedure for Data Lake Relational Engine

Reports detailed usage information for tables accessed by the workload.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqtableuse
```



<a name="loioa5bae03284f210159da88fd013c0d1ee__section_z4k_lsm_nbb"/>

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

Table name.



</td>
</tr>
<tr>
<td valign="top">

Owner



</td>
<td valign="top">

User name of table owner.



</td>
</tr>
<tr>
<td valign="top">

UID



</td>
<td valign="top">

Table unique identifier. UID is a number assigned by the system that uniquely identifies the instance of the table \(where instance is defined when an object is created\).



</td>
</tr>
<tr>
<td valign="top">

LastDT



</td>
<td valign="top">

Date/time of last access.



</td>
</tr>
<tr>
<td valign="top">

NRef



</td>
<td valign="top">

Number of query references.



</td>
</tr>
</table>



<a name="loioa5bae03284f210159da88fd013c0d1ee__iq_refbb_1813"/>

## Remarks

Tables created in SYSTEM are not reported.



<a name="loioa5bae03284f210159da88fd013c0d1ee__iq_refbb_1812"/>

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

**Related Information**  


[sp\_iqcolumnuse Procedure for Data Lake Relational Engine](sp-iqcolumnuse-procedure-for-data-lake-relational-engine-a59fb88.md "Reports detailed usage information for columns accessed by the workload.")

[sp\_iqindexadvice Procedure for Data Lake Relational Engine](sp-iqindexadvice-procedure-for-data-lake-relational-engine-a5ab8bc.md "Displays stored index advice messages. Optionally clears advice storage.")

[sp\_iqindexuse Procedure for Data Lake Relational Engine](sp-iqindexuse-procedure-for-data-lake-relational-engine-a5ae206.md "Reports detailed usage information for secondary (non-FP) indexes accessed by the workload.")

[sp\_iqunusedcolumn Procedure for Data Lake Relational Engine](sp-iqunusedcolumn-procedure-for-data-lake-relational-engine-a5bbef3.md "Reports IQ columns that were not referenced by the workload.")

[sp\_iqunusedindex Procedure for Data Lake Relational Engine](sp-iqunusedindex-procedure-for-data-lake-relational-engine-a5bc6ce.md "Reports IQ secondary (non-FP) indexes that were not referenced by the workload.")

[sp\_iqunusedtable Procedure for Data Lake Relational Engine](sp-iqunusedtable-procedure-for-data-lake-relational-engine-a5bced3.md "Reports IQ tables that were not referenced by the workload.")

[sp\_iqworkmon Procedure for Data Lake Relational Engine](sp-iqworkmon-procedure-for-data-lake-relational-engine-a5c13d2.md "Controls collection of workload monitor usage information, and reports monitoring collection status. sp_iqworkmon collects information only for queries (SQL statements containing a FROM clause). You cannot use sp_iqworkmon for INSERT or LOAD statements.")

