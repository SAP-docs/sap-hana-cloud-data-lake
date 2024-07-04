<!-- loioa5c13d2284f2101582a2d95ea5541a11 -->

# sp\_iqworkmon System Procedure for Data Lake Relational Engine

Controls collection of workload monitor usage information, and reports monitoring collection status. sp\_iqworkmon collects information only for queries \(SQL statements containing a FROM clause\). You cannot use sp\_iqworkmon for INSERT or LOAD statements.



<a name="loioa5c13d2284f2101582a2d95ea5541a11__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqworkmon [ '<action>' [ , '<mode>' ] ]
```



<a name="loioa5c13d2284f2101582a2d95ea5541a11__section_h5b_n3m_nbb"/>

## Parameters


<dl>
<dt><b>

*<action\>*

</b></dt>
<dd>

Specifies the control action to apply by using one of the following values:

```
<action> ::=
   { start
   | stop
   | status
   | reset }
```


<dl>
<dt><b>

start

</b></dt>
<dd>

Starts monitoring for the specified mode immediately.



</dd><dt><b>

stop

</b></dt>
<dd>

Stops monitoring immediately.



</dd><dt><b>

status

</b></dt>
<dd>

\(default\) Displays the current status without changing the state.



</dd><dt><b>

reset

</b></dt>
<dd>

Clears the statistics



</dd>
</dl>

The statistics are persisted until they are cleared with the reset argument, or until the server is restarted. Statistics collection does not automatically resume after a server restart, and it needs to be restarted using start.



</dd><dt><b>

*<mode\>*

</b></dt>
<dd>

Specifies the type of monitoring to control. *<mode\>* cannot be specified without an *<action\>*.

```
<mode> ::=
   { index
   | table
   | column
   | all }
```

The INDEX, TABLE, and COLUMN keywords individually control monitoring of index usage, table usage, and column usage respectively. ALL \(default\) controls monitoring of all usage monitoring features simultaneously.



</dd>
</dl>



<a name="loioa5c13d2284f2101582a2d95ea5541a11__section_tb1_m3m_nbb"/>

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

MonMode

</td>
<td valign="top">

Table, index, or column

</td>
</tr>
<tr>
<td valign="top">

Status

</td>
<td valign="top">

Started or stopped

</td>
</tr>
<tr>
<td valign="top">

Rowcount

</td>
<td valign="top">

Current number of rows collected

</td>
</tr>
</table>



<a name="loioa5c13d2284f2101582a2d95ea5541a11__iq_refbb_1860"/>

## Remarks

Usage is collected only for SQL statements containing a FROM clause; for example, SELECT, UPDATE, and DELETE.



<a name="loioa5c13d2284f2101582a2d95ea5541a11__iq_refbb_1859"/>

## Privileges

Requires all of the following:

-   EXECUTE object-level privilege on this procedure
-   MONITOR system privilege



## Side Effects

None.



<a name="loioa5c13d2284f2101582a2d95ea5541a11__iq_refbb_1863"/>

## Examples

This example returns output from this procedure:

```
CALL sp_iqworkmon ('status' , 'all' );
```


<table>
<tr>
<th valign="top">

MonMode

</th>
<th valign="top">

Status

</th>
<th valign="top">

Rowcount

</th>
</tr>
<tr>
<td valign="top">

index

</td>
<td valign="top">

stopped

</td>
<td valign="top">

15

</td>
</tr>
<tr>
<td valign="top">

table

</td>
<td valign="top">

started

</td>
<td valign="top">

10

</td>
</tr>
<tr>
<td valign="top">

column

</td>
<td valign="top">

stopped

</td>
<td valign="top">

31

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

[sp\_iqunusedtable System Procedure for Data Lake Relational Engine](sp-iqunusedtable-system-procedure-for-data-lake-relational-engine-a5bced3.md "Reports tables that were not referenced by the workload.")

