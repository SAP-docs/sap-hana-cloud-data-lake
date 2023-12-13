<!-- loioa5ab8bc984f2101593388431a4a60c82 -->

# sp\_iqindexadvice Procedure for Data Lake Relational Engine

Displays stored index advice messages. Optionally clears advice storage.



<a name="loioa5ab8bc984f2101593388431a4a60c82__section_qpw_pwh_b4b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqindexadvice ( [ <resetflag> ] );
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



<a name="loioa5ab8bc984f2101593388431a4a60c82__iq_refbb_1599"/>

## Remarks

Allows users to query aggregated index advisor messages using SQL. The information can help you decide which indexes or schema changes will affect the most queries.

> ### Note:  
> The index advice derives from a single query at a single point in time. The index advice doesn't take any other factors into account.
> 
> Consider the index advice carefully before acting on it. Adding indexes can improve query speed, but at the cost of load performance. Your query improvement may not be worth the costs of loading into more indexes, and the costs of working with a larger object.

`INDEX_ADVISOR` columns are:

-   Advice – unique advice message
-   NInst – number of instances of message
-   LastDT – last date/time advice was generated



<a name="loioa5ab8bc984f2101593388431a4a60c82__iq_refbb_1596"/>

## Privileges

Requires EXECUTE object-level privilege on the procedure, along with one of the following:

-   ALTER ANY INDEX system privilege
-   ALTER ANY OBJECT system privilege



<a name="loioa5ab8bc984f2101593388431a4a60c82__section_kdt_jc1_nbb"/>

## Side Effects

None



<a name="loioa5ab8bc984f2101593388431a4a60c82__iq_refbb_1600"/>

## Examples

The following shows sample output from the sp\_iqindexadvice procedure:


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


[sp\_iqcolumnuse Procedure for Data Lake Relational Engine](sp-iqcolumnuse-procedure-for-data-lake-relational-engine-a59fb88.md "Reports detailed usage information for columns accessed by the workload.")

[sp\_iqindexuse Procedure for Data Lake Relational Engine](sp-iqindexuse-procedure-for-data-lake-relational-engine-a5ae206.md "Reports detailed usage information for secondary (non-FP) indexes accessed by the workload.")

[sp\_iqtableuse Procedure for Data Lake Relational Engine](sp-iqtableuse-procedure-for-data-lake-relational-engine-a5bae03.md "Reports detailed usage information for tables accessed by the workload.")

[sp\_iqunusedcolumn Procedure for Data Lake Relational Engine](sp-iqunusedcolumn-procedure-for-data-lake-relational-engine-a5bbef3.md "Reports columns that were not referenced by the workload.")

[sp\_iqunusedindex Procedure for Data Lake Relational Engine](sp-iqunusedindex-procedure-for-data-lake-relational-engine-a5bc6ce.md "Reports secondary (non-FP) indexes that were not referenced by the workload.")

[sp\_iqunusedtable Procedure for Data Lake Relational Engine](sp-iqunusedtable-procedure-for-data-lake-relational-engine-a5bced3.md "Reports tables that were not referenced by the workload.")

[sp\_iqworkmon Procedure for Data Lake Relational Engine](sp-iqworkmon-procedure-for-data-lake-relational-engine-a5c13d2.md "Controls collection of workload monitor usage information, and reports monitoring collection status. sp_iqworkmon collects information only for queries (SQL statements containing a FROM clause). You cannot use sp_iqworkmon for INSERT or LOAD statements.")

