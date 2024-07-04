<!-- loio3be5b0046c5f10148d0cfa4686fbb0ce -->

# sa\_disk\_free\_space System Procedure for Data Lake Relational Engine

Reports information about space available for a transaction log, transaction log mirror, and/or temporary file.



<a name="loio3be5b0046c5f10148d0cfa4686fbb0ce__section_idn_b13_b4b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sa_disk_free_space( [ <p_dbspace_name> ] )
```



## Parameters


<dl>
<dt><b>

*<p\_dbspace\_name\>* 

</b></dt>
<dd>

Use this VARCHAR\(128\) parameter to specify the name of a transaction log file, transaction log mirror file, or temporary file. The default is NULL.

Specify SYSTEM to get information about the main database file, TEMPORARY or TEMP to get information about the temporary file, TRANSLOG to get information about the transaction log, or TRANSLOGMIRROR to get information about the transaction log mirror.



</dd>
</dl>



## Result Set


<table>
<tr>
<th valign="top">

Column name

</th>
<th valign="top">

Data type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

dbspace\_name

</td>
<td valign="top">

VARCHAR\(128\)

</td>
<td valign="top">

This is the transaction log file, transaction log mirror file, or temporary file.

</td>
</tr>
<tr>
<td valign="top">

free\_space

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

The number of free bytes on the volume.

</td>
</tr>
<tr>
<td valign="top">

total\_space

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

The total amount of space available on the drive.

</td>
</tr>
</table>



## Remarks

If the *<p\_dbspace\_name\>* parameter is not specified or is NULL, then the result set contains one row for each of the transaction log, transaction log mirror, and temporary file, if they exist. If *<p\_dbspace\_name\>* is specified, then exactly one or zero rows are returned \(zero if log or mirror is specified and there is no log or mirror file\).



## Privileges

Requires all of the following:

-   EXECUTE object-level privilege on this procedure
-   MANAGE ANY DBSPACE system privilege.



## Side Effects

None.



## Examples

This example returns a result set containing information about available space.

```
CALL sa_disk_free_space( );
```


<table>
<tr>
<th valign="top">

dbspace\_name

</th>
<th valign="top">

free\_space

</th>
<th valign="top">

total\_space

</th>
</tr>
<tr>
<td valign="top">

system

</td>
<td valign="top">

513628426240

</td>
<td valign="top">

517290852352

</td>
</tr>
<tr>
<td valign="top">

translog

</td>
<td valign="top">

513628426240

</td>
<td valign="top">

517290852352

</td>
</tr>
<tr>
<td valign="top">

temporary

</td>
<td valign="top">

11332939776

</td>
<td valign="top">

21440212992

</td>
</tr>
</table>

