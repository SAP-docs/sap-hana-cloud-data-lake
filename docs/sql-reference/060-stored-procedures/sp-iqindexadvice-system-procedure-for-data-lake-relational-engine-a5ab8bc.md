<!-- loioa5ab8bc984f2101593388431a4a60c82 -->

# sp\_iqindexadvice System Procedure for Data Lake Relational Engine

Displays stored index advice messages. Optionally clears advice storage.



<a name="loioa5ab8bc984f2101593388431a4a60c82__section_qpw_pwh_b4b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqindexadvice ( [ <resetflag> ] )
```



<a name="loioa5ab8bc984f2101593388431a4a60c82__iq_refbb_1597"/>

## Parameters


<dl>
<dt><b>

*<resetflag\>*

</b></dt>
<dd>

Lets the caller clear the index advice storage. If *<resetflag\>* is nonzero, all advice is removed after the last row has been retrieved.



</dd>
</dl>



<a name="loioa5ab8bc984f2101593388431a4a60c82__section_w4p_c23_vzb"/>

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

Advice

</td>
<td valign="top">

Displays a unique advice message.

</td>
</tr>
<tr>
<td valign="top">

NInst

</td>
<td valign="top">

Displays the number of instances of message.

</td>
</tr>
<tr>
<td valign="top">

LastDT

</td>
<td valign="top">

Displays the last date and time advice was generated.

</td>
</tr>
</table>



<a name="loioa5ab8bc984f2101593388431a4a60c82__iq_refbb_1599"/>

## Remarks

Allows users to query aggregated index advisor messages using SQL. The information can help you decide which indexes or schema changes will affect the most queries.

The index advice derives from a single query at a single point in time. The index advice doesn't take any other factors into account.

Consider the index advice carefully before acting on it. Adding indexes can improve query speed, but at the cost of load performance. Your query improvement may not be worth the costs of loading into more indexes, and the costs of working with a larger object.



<a name="loioa5ab8bc984f2101593388431a4a60c82__iq_refbb_1596"/>

## Privileges

Requires EXECUTE object-level privilege on this procedure along with one of the following:

-   ALTER ANY INDEX system privilege
-   ALTER ANY OBJECT system privilege



<a name="loioa5ab8bc984f2101593388431a4a60c82__section_kdt_jc1_nbb"/>

## Side Effects

None.



<a name="loioa5ab8bc984f2101593388431a4a60c82__iq_refbb_1600"/>

## Examples

This example returns stored index advice messages.

```
CALL sp_iqindexadvice;
```


<table>
<tr>
<th valign="top">

Advice

</th>
<th valign="top">

NInst

</th>
<th valign="top">

LastDT

</th>
</tr>
<tr>
<td valign="top">

Add a CMP index on DBA.tb \(c2, c3\) Predicate: \(tb.c2 = tb.c3\)

</td>
<td valign="top">

2073

</td>
<td valign="top">

2009-04-07 16:37:31.000

</td>
</tr>
<tr>
<td valign="top">

Convert HG index on DBA.tb.c4 to a unique HG

</td>
<td valign="top">

812

</td>
<td valign="top">

2009-04-06 10:01:15.000

</td>
</tr>
<tr>
<td valign="top">

Join Key Columns DBA.ta.c1 and DBA.tb.c1 have mismatched data types

</td>
<td valign="top">

911

</td>
<td valign="top">

2009-02-25 20:59:01.000

</td>
</tr>
</table>

**Related Information**  


[sp\_iqcolumnuse System Procedure for Data Lake Relational Engine](sp-iqcolumnuse-system-procedure-for-data-lake-relational-engine-a59fb88.md "Reports detailed usage information for columns accessed by the workload.")

[sp\_iqindexuse System Procedure for Data Lake Relational Engine](sp-iqindexuse-system-procedure-for-data-lake-relational-engine-a5ae206.md "Reports detailed usage information for secondary (non-FP) indexes accessed by the workload.")

[sp\_iqtableuse System Procedure for Data Lake Relational Engine](sp-iqtableuse-system-procedure-for-data-lake-relational-engine-a5bae03.md "Reports detailed usage information for tables accessed by the workload.")

[sp\_iqunusedcolumn System Procedure for Data Lake Relational Engine](sp-iqunusedcolumn-system-procedure-for-data-lake-relational-engine-a5bbef3.md "Reports columns that were not referenced by the workload.")

[sp\_iqunusedindex System Procedure for Data Lake Relational Engine](sp-iqunusedindex-system-procedure-for-data-lake-relational-engine-a5bc6ce.md "Reports secondary (non-FP) indexes that were not referenced by the workload.")

[sp\_iqunusedtable System Procedure for Data Lake Relational Engine](sp-iqunusedtable-system-procedure-for-data-lake-relational-engine-a5bced3.md "Reports tables that were not referenced by the workload.")

[sp\_iqworkmon System Procedure for Data Lake Relational Engine](sp-iqworkmon-system-procedure-for-data-lake-relational-engine-a5c13d2.md "Controls collection of workload monitor usage information, and reports monitoring collection status. sp_iqworkmon collects information only for queries (SQL statements containing a FROM clause). You cannot use sp_iqworkmon for INSERT or LOAD statements.")

