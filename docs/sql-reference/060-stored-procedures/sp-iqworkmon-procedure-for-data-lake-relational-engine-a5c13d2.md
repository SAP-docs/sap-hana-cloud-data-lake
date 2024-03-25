<!-- loioa5c13d2284f2101582a2d95ea5541a11 -->

# sp\_iqworkmon Procedure for Data Lake Relational Engine

Controls collection of workload monitor usage information, and reports monitoring collection status. sp\_iqworkmon collects information only for queries \(SQL statements containing a FROM clause\). You cannot use sp\_iqworkmon for INSERT or LOAD statements.



<a name="loioa5c13d2284f2101582a2d95ea5541a11__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqworkmon [ '<action>' ] [ , '<mode>' ]
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
   'start' , 'stop' , 'status' , 'reset'
```

-   start – starts monitoring for the specified mode immediately.
-   stop – stops monitoring immediately.
-   status – \(default\) displays the current status without changing state.
-   reset – clears the statistics.

The statistics are persisted until they are cleared with the reset argument, or until the server is restarted. Statistics collection does not automatically resume after a server restart, and it needs to be restarted using start.



</dd><dt><b>

*<mode\>*

</b></dt>
<dd>

Specifies the type of monitoring to control.

```
<mode> ::=
    'index' , 'table' , 'column ' , 'all'
```

The INDEX, TABLE, and COLUMN keywords individually control monitoring of index usage, table usage, and column usage respectively. The default ALL keyword controls monitoring of all usage monitoring features simultaneously.



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

There is always a result set when you execute sp\_iqworkmon. If you specify a specific mode \(such as index\), only the row for that mode appears.

Usage is collected only for SQL statements containing a FROM clause; for example, SELECT, UPDATE, and DELETE.

If one argument is specified, it can only be *<action\>*. For example:

```
sp_iqworkmon 'stop'
```



<a name="loioa5c13d2284f2101582a2d95ea5541a11__iq_refbb_1859"/>

## Privileges

Requires EXECUTE object-level privilege on the procedure along with the MONITOR system privilege.



## Side Effects

None



<a name="loioa5c13d2284f2101582a2d95ea5541a11__iq_refbb_1863"/>

## Examples

The following example displays output from the sp\_iqworkmon procedure:

```
CALL sp_iqworkmon ('start' , 'all' );
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

started

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

started

</td>
<td valign="top">

31

</td>
</tr>
</table>

**Related Information**  


[sp\_iqcolumnuse Procedure for Data Lake Relational Engine](sp-iqcolumnuse-procedure-for-data-lake-relational-engine-a59fb88.md "Reports detailed usage information for columns accessed by the workload.")

[sp\_iqindexadvice Procedure for Data Lake Relational Engine](sp-iqindexadvice-procedure-for-data-lake-relational-engine-a5ab8bc.md "Displays stored index advice messages. Optionally clears advice storage.")

[sp\_iqindexuse Procedure for Data Lake Relational Engine](sp-iqindexuse-procedure-for-data-lake-relational-engine-a5ae206.md "Reports detailed usage information for secondary (non-FP) indexes accessed by the workload.")

[sp\_iqtableuse Procedure for Data Lake Relational Engine](sp-iqtableuse-procedure-for-data-lake-relational-engine-a5bae03.md "Reports detailed usage information for tables accessed by the workload.")

[sp\_iqunusedcolumn Procedure for Data Lake Relational Engine](sp-iqunusedcolumn-procedure-for-data-lake-relational-engine-a5bbef3.md "Reports columns that were not referenced by the workload.")

[sp\_iqunusedindex Procedure for Data Lake Relational Engine](sp-iqunusedindex-procedure-for-data-lake-relational-engine-a5bc6ce.md "Reports secondary (non-FP) indexes that were not referenced by the workload.")

[sp\_iqunusedtable Procedure for Data Lake Relational Engine](sp-iqunusedtable-procedure-for-data-lake-relational-engine-a5bced3.md "Reports tables that were not referenced by the workload.")

