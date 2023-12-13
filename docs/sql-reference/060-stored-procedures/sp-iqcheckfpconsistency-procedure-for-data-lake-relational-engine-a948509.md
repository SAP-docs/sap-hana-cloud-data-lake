<!-- loioa948509b70dc4210a83bb773eb91dde5 -->

# sp\_iqcheckfpconsistency Procedure for Data Lake Relational Engine

Checks consistency of default indexes created on table columns.



<a name="loioa948509b70dc4210a83bb773eb91dde5__section_isv_cwh_b4b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqcheckfpconsistency ( <table_name>, <column_name>, <table_owner> );
```



<a name="loioa948509b70dc4210a83bb773eb91dde5__iq_refbb_1513"/>

## Parameters


<dl>
<dt><b>

*<table\_name\>*

</b></dt>
<dd>

The name of the table that you want to check.



</dd><dt><b>

*<column\_name\>*

</b></dt>
<dd>

The name of the column to check.



</dd><dt><b>

*<table\_owner\>*

</b></dt>
<dd>

The name of the owner of tables to check.



</dd>
</dl>



<a name="loioa948509b70dc4210a83bb773eb91dde5__section_pxx_k3n_zyb"/>

## Result Set


<table>
<tr>
<th valign="top">

Value

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

table\_owner

</td>
<td valign="top">

The owner of the table being checked.

</td>
</tr>
<tr>
<td valign="top">

table\_name

</td>
<td valign="top">

The name of the table being checked.

</td>
</tr>
<tr>
<td valign="top">

column\_name

</td>
<td valign="top">

The name of the column being checked.

</td>
</tr>
<tr>
<td valign="top">

status

</td>
<td valign="top">

The status of the column being checked.

</td>
</tr>
</table>



<a name="loioa948509b70dc4210a83bb773eb91dde5__iq_refbb_1561"/>

## Remarks

When you create a table, data lake Relational Engine assigns a default index to each new column. This procedure checks these indexes and diagnoses corrupted tables and columns.

The procedure returns a result table that provides a summary report. If data lake Relational Engine detects errors, it returns detailed error messages in the data lake Relational Engine message file.

Currently there is no consistency verification for columns with BIT data types. The report returns "No Errors Detected," but does not actually verify them.



## Privileges

Requires EXECUTE object-level privilege on the procedure.



## Side Effects

None



## Examples

This example uses the sp\_iqcheckfpconsistency system procedure to check the consistency for all columns in table mytable:

```
call sp_iqcheckfpconsistency('mytable');
```


<table>
<tr>
<th valign="top">

table\_owner

</th>
<th valign="top">

table\_name

</th>
<th valign="top">

column\_name

</th>
<th valign="top">

status

</th>
</tr>
<tr>
<td valign="top">

USER1

</td>
<td valign="top">

mytable

</td>
<td valign="top">

ColA

</td>
<td valign="top">

No Errors Detected

</td>
</tr>
<tr>
<td valign="top">

USER1

</td>
<td valign="top">

mytable

</td>
<td valign="top">

ColB

</td>
<td valign="top">

Errors Detected

</td>
</tr>
<tr>
<td valign="top">

USER1

</td>
<td valign="top">

mytable

</td>
<td valign="top">

ColC

</td>
<td valign="top">

No Errors Detected

</td>
</tr>
<tr>
<td valign="top">

...

</td>
<td valign="top">

...

</td>
<td valign="top">

…

</td>
<td valign="top">

...

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

See the data lake Relational Engine message file for detail error messages

</td>
</tr>
</table>

