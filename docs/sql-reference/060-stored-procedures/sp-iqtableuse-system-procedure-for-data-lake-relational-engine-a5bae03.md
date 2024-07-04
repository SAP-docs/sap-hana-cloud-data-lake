<!-- loioa5bae03284f210159da88fd013c0d1ee -->

# sp\_iqtableuse System Procedure for Data Lake Relational Engine

Reports detailed usage information for tables accessed by the workload.



<a name="loioa5bae03284f210159da88fd013c0d1ee__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqtableuse
```



<a name="loioa5bae03284f210159da88fd013c0d1ee__section_tkv_5w3_yyb"/>

## Parameters

None.



<a name="loioa5bae03284f210159da88fd013c0d1ee__section_z4k_lsm_nbb"/>

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

Requires all of the following

-   EXECUTE object-level privilege on this procedure
-   MONITOR system privilege



## Side Effects

None.



<a name="loioa5bae03284f210159da88fd013c0d1ee__section_e2g_rpy_kbc"/>

## Examples

```
--- Setup for the following examples ---
CALL sp_iqworkmon ('start', 'all');
SELECT * FROM HDLADMIN.T1, USER1,A1;
CALL sp_iqworkmon ('stop');
```

This example returns usage information for all tables accessed by the workload.

```
CALL sp_iqtableuse;
```


<table>
<tr>
<th valign="top">

TableName

</th>
<th valign="top">

Owner

</th>
<th valign="top">

UID

</th>
<th valign="top">

LastDT

</th>
<th valign="top">

NRef

</th>
</tr>
<tr>
<td valign="top">

T1

</td>
<td valign="top">

HDLADMIN

</td>
<td valign="top">

12382

</td>
<td valign="top">

20:41.7

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

A1

</td>
<td valign="top">

USER1

</td>
<td valign="top">

17170

</td>
<td valign="top">

21:57.6

</td>
<td valign="top">

1

</td>
</tr>
</table>

**Related Information**  


[sp\_iqcolumnuse System Procedure for Data Lake Relational Engine](sp-iqcolumnuse-system-procedure-for-data-lake-relational-engine-a59fb88.md "Reports detailed usage information for columns accessed by the workload.")

[sp\_iqindexadvice System Procedure for Data Lake Relational Engine](sp-iqindexadvice-system-procedure-for-data-lake-relational-engine-a5ab8bc.md "Displays stored index advice messages. Optionally clears advice storage.")

[sp\_iqindexuse System Procedure for Data Lake Relational Engine](sp-iqindexuse-system-procedure-for-data-lake-relational-engine-a5ae206.md "Reports detailed usage information for secondary (non-FP) indexes accessed by the workload.")

[sp\_iqunusedcolumn System Procedure for Data Lake Relational Engine](sp-iqunusedcolumn-system-procedure-for-data-lake-relational-engine-a5bbef3.md "Reports columns that were not referenced by the workload.")

[sp\_iqunusedindex System Procedure for Data Lake Relational Engine](sp-iqunusedindex-system-procedure-for-data-lake-relational-engine-a5bc6ce.md "Reports secondary (non-FP) indexes that were not referenced by the workload.")

[sp\_iqunusedtable System Procedure for Data Lake Relational Engine](sp-iqunusedtable-system-procedure-for-data-lake-relational-engine-a5bced3.md "Reports tables that were not referenced by the workload.")

[sp\_iqworkmon System Procedure for Data Lake Relational Engine](sp-iqworkmon-system-procedure-for-data-lake-relational-engine-a5c13d2.md "Controls collection of workload monitor usage information, and reports monitoring collection status. sp_iqworkmon collects information only for queries (SQL statements containing a FROM clause). You cannot use sp_iqworkmon for INSERT or LOAD statements.")

