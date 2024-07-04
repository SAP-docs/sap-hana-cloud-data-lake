<!-- loioa5bced3184f2101594668a0e1dd0375a -->

# sp\_iqunusedtable System Procedure for Data Lake Relational Engine

Reports tables that were not referenced by the workload.



<a name="loioa5bced3184f2101594668a0e1dd0375a__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqunusedtable
```



<a name="loioa5bced3184f2101594668a0e1dd0375a__section_wnm_sxc_yyb"/>

## Parameters

None.



<a name="loioa5bced3184f2101594668a0e1dd0375a__section_vxr_h4m_nbb"/>

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

Owner

</td>
<td valign="top">

User name of index owner

</td>
</tr>
</table>



<a name="loioa5bced3184f2101594668a0e1dd0375a__iq_refbb_1832"/>

## Remarks

Tables created in SYSTEM and local temporary tables are not reported.



<a name="loioa5bced3184f2101594668a0e1dd0375a__iq_refbb_1831"/>

## Privileges

Requires EXECUTE object-level privilege on the procedure, along with the MONITOR system privilege.



## Side Effects

None.



<a name="loioa5bced3184f2101594668a0e1dd0375a__iq_refbb_1834"/>

## Examples

This example returns a list of the tables not referenced by the workload.

```
CALL sp_iqunusedtable;
```


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

t1

</td>
<td valign="top">

HDLADMIN

</td>
</tr>
<tr>
<td valign="top">

m\_t1

</td>
<td valign="top">

HDLADMIN

</td>
</tr>
<tr>
<td valign="top">

table1

</td>
<td valign="top">

HDLADMIN

</td>
</tr>
<tr>
<td valign="top">

mytable

</td>
<td valign="top">

HDLADMIN

</td>
</tr>
<tr>
<td valign="top">

A1

</td>
<td valign="top">

USER1

</td>
</tr>
<tr>
<td valign="top">

A2

</td>
<td valign="top">

USER1

</td>
</tr>
<tr>
<td valign="top">

P3

</td>
<td valign="top">

USER2

</td>
</tr>
<tr>
<td valign="top">

P4

</td>
<td valign="top">

USER2

</td>
</tr>
<tr>
<td valign="top">

D1

</td>
<td valign="top">

USER3

</td>
</tr>
<tr>
<td valign="top">

D3

</td>
<td valign="top">

USER3

</td>
</tr>
</table>

**Related Information**  


[sp\_iqcolumnuse System Procedure for Data Lake Relational Engine](sp-iqcolumnuse-system-procedure-for-data-lake-relational-engine-a59fb88.md "Reports detailed usage information for columns accessed by the workload.")

[sp\_iqindexadvice System Procedure for Data Lake Relational Engine](sp-iqindexadvice-system-procedure-for-data-lake-relational-engine-a5ab8bc.md "Displays stored index advice messages. Optionally clears advice storage.")

[sp\_iqindexuse System Procedure for Data Lake Relational Engine](sp-iqindexuse-system-procedure-for-data-lake-relational-engine-a5ae206.md "Reports detailed usage information for secondary (non-FP) indexes accessed by the workload.")

[sp\_iqtableuse System Procedure for Data Lake Relational Engine](sp-iqtableuse-system-procedure-for-data-lake-relational-engine-a5bae03.md "Reports detailed usage information for tables accessed by the workload.")

[sp\_iqunusedcolumn System Procedure for Data Lake Relational Engine](sp-iqunusedcolumn-system-procedure-for-data-lake-relational-engine-a5bbef3.md "Reports columns that were not referenced by the workload.")

[sp\_iqunusedindex System Procedure for Data Lake Relational Engine](sp-iqunusedindex-system-procedure-for-data-lake-relational-engine-a5bc6ce.md "Reports secondary (non-FP) indexes that were not referenced by the workload.")

[sp\_iqworkmon System Procedure for Data Lake Relational Engine](sp-iqworkmon-system-procedure-for-data-lake-relational-engine-a5c13d2.md "Controls collection of workload monitor usage information, and reports monitoring collection status. sp_iqworkmon collects information only for queries (SQL statements containing a FROM clause). You cannot use sp_iqworkmon for INSERT or LOAD statements.")

