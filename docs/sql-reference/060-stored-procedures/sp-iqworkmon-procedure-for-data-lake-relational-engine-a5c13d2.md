<!-- loioa5c13d2284f2101582a2d95ea5541a11 -->

# sp\_iqworkmon Procedure for Data Lake Relational Engine

Controls collection of workload monitor usage information, and reports monitoring collection status. sp\_iqworkmon collects information only for queries \(SQL statements containing a FROM clause\). You cannot use sp\_iqworkmon for INSERT or LOAD statements.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqworkmon [ '<action>' ] [ , '<mode>' ]
```

```
<action> ::=
   'start' , 'stop' , 'status' , 'reset'
```

```
<mode> ::=
    'index' , 'table' , 'column ' , 'all'
```



<a name="loioa5c13d2284f2101582a2d95ea5541a11__section_h5b_n3m_nbb"/>

## Parameters

 *<action\>*
 :   Specifies the control action to apply by using one of the following values:

    -   start – starts monitoring for the specified mode immediately.
    -   stop – stops monitoring immediately.
    -   status – \(default\) displays the current status without changing state.
    -   reset – clears the statistics.

    The statistics are persisted until they are cleared with the reset argument, or until the server is restarted. Statistics collection does not automatically resume after a server restart, and it needs to be restarted using start.

  *<mode\>*
 :   Specifies the type of monitoring to control. The INDEX, TABLE, and COLUMN keywords individually control monitoring of index usage, table usage, and column usage respectively. The default ALL keyword controls monitoring of all usage monitoring features simultaneously.

 

<a name="loioa5c13d2284f2101582a2d95ea5541a11__section_tb1_m3m_nbb"/>

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



<a name="loioa5c13d2284f2101582a2d95ea5541a11__iq_refbb_1863"/>

## Example

The following example displays output from the sp\_iqworkmon procedure:

```
sp_iqworkmon 'start' , 'all' 
```

```
MonMode     Status      Rowcount 
index       started     15 
table       started     10
column      started     31
```

**Related Information**  


[sp\_iqcolumnuse Procedure for Data Lake Relational Engine](sp-iqcolumnuse-procedure-for-data-lake-relational-engine-a59fb88.md "Reports detailed usage information for columns accessed by the workload.")

[sp\_iqindexadvice Procedure for Data Lake Relational Engine](sp-iqindexadvice-procedure-for-data-lake-relational-engine-a5ab8bc.md "Displays stored index advice messages. Optionally clears advice storage.")

[sp\_iqindexuse Procedure for Data Lake Relational Engine](sp-iqindexuse-procedure-for-data-lake-relational-engine-a5ae206.md "Reports detailed usage information for secondary (non-FP) indexes accessed by the workload.")

[sp\_iqtableuse Procedure for Data Lake Relational Engine](sp-iqtableuse-procedure-for-data-lake-relational-engine-a5bae03.md "Reports detailed usage information for tables accessed by the workload.")

[sp\_iqunusedcolumn Procedure for Data Lake Relational Engine](sp-iqunusedcolumn-procedure-for-data-lake-relational-engine-a5bbef3.md "Reports IQ columns that were not referenced by the workload.")

[sp\_iqunusedindex Procedure for Data Lake Relational Engine](sp-iqunusedindex-procedure-for-data-lake-relational-engine-a5bc6ce.md "Reports IQ secondary (non-FP) indexes that were not referenced by the workload.")

[sp\_iqunusedtable Procedure for Data Lake Relational Engine](sp-iqunusedtable-procedure-for-data-lake-relational-engine-a5bced3.md "Reports IQ tables that were not referenced by the workload.")
