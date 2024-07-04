<!-- loioa5ba627c84f2101591d9cedf0830a4e0 -->

# sp\_iqtablesize System Procedure for Data Lake Relational Engine

Returns the size of the specified table.



<a name="loioa5ba627c84f2101591d9cedf0830a4e0__section_p4t_vqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqtablesize ( <table_owner>.<table_name> )
```



<a name="loioa5ba627c84f2101591d9cedf0830a4e0__sp_iqtablesize_parm1"/>

## Parameters


<dl>
<dt><b>

*<table\_owner\>*

</b></dt>
<dd>

The owner of the table.



</dd><dt><b>

*<table\_name\>*

</b></dt>
<dd>

The name of the table.



</dd>
</dl>



<a name="loioa5ba627c84f2101591d9cedf0830a4e0__sp_iqtablesize_returns1"/>

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

Ownername

</td>
<td valign="top">

The name of owner.

</td>
</tr>
<tr>
<td valign="top">

Tablename

</td>
<td valign="top">

The name of table.

</td>
</tr>
<tr>
<td valign="top">

Columns

</td>
<td valign="top">

The number of columns in the table.

</td>
</tr>
<tr>
<td valign="top">

KBytes

</td>
<td valign="top">

An approximation of the physical table size, in kilobytes. Data lake Relational Engine uses a 512KB page size and the size in KB reported by sp\_iqtablesize is based on a heuristic for the average page size in the cloud dbspace.

</td>
</tr>
<tr>
<td valign="top">

Pages

</td>
<td valign="top">

The number of data lake Relational Engine pages needed to hold the table in memory. Pages is the total number of data lake Relational Engine pages for the table. The unit of measurement for pages is page size. All in-memory buffers \(buffers in the data lake Relational Engine buffer cache\) are the same size.

</td>
</tr>
<tr>
<td valign="top">

CompressedPages

</td>
<td valign="top">

The number of data lake Relational Engine pages that are compressed, when the table is compressed \(on disk\). Pages on disk are compressed. For example, if Pages is 1000 and CompressedPages is 992, this means that 992 of the 1000 pages are compressed. CompressedPages divided by Pages is usually near 100%, because most pages compress. An empty page is not compressed, since data lake Relational Engine does not write empty pages. Data lake Relational Engine pages compress well, regardless of the fullness of the page.

</td>
</tr>
<tr>
<td valign="top">

NBlocks

</td>
<td valign="top">

The number of data lake Relational Engine blocks. NBlocks is Kbytes divided by block size. Each data lake Relational Engine page on disk uses 1 to 16 blocks.

</td>
</tr>
<tr>
<td valign="top">

RlvLogPages

</td>
<td valign="top">

For internal use.

</td>
</tr>
<tr>
<td valign="top">

RlvLogBytes

</td>
<td valign="top">

For internal use.

</td>
</tr>
</table>



<a name="loioa5ba627c84f2101591d9cedf0830a4e0__sp_iqtablesize_remarks1"/>

## Remarks

Returns the total size of the table in KBytes and NBlocks \(data lake Relational Engine blocks\). Also returns the number of pages required to hold the table in memory, and the number of data lake Relational Engine pages that are compressed when the table is compressed \(on disk\). You need to specify the *<table\_name\>* parameter with this procedure. If you are the owner of *<table\_name\>*, then you do not have to specify the *<table\_owner\>* parameter.

> ### Note:  
> Data lake Relational Engine always reads and writes an entire page, not blocks. For example, if an individual page compresses to 88 KB, then data lake Relational Engine reads and writes the 88 KB in one I/O. The average page is compressed by a factor of 2 to 3.



<a name="loioa5ba627c84f2101591d9cedf0830a4e0__sp_iqtablesize_priv1"/>

## Privileges



### 

Requires EXECUTE object-level privilege on this procedure, along with one of the following:

-   You own the table
-   MANAGE ANY DBSPACE system privilege
-   ALTER ANY TABLE system privilege



<a name="loioa5ba627c84f2101591d9cedf0830a4e0__sp_iqtablesize_sideeffects1"/>

## Side Effects

None.



<a name="loioa5ba627c84f2101591d9cedf0830a4e0__sp_iqtablesize_example1"/>

## Examples

This example returns information on the size of table A1, owned by USER1.

```
CALL sp_iqtablesize ('USER1.A1');
```


<table>
<tr>
<th valign="top">

Owner

name

</th>
<th valign="top">

Table

name

</th>
<th valign="top">

Columns

</th>
<th valign="top">

KBytes

</th>
<th valign="top">

Pages

</th>
<th valign="top">

Pages

</th>
<th valign="top">

Compressed

Pages

</th>
<th valign="top">

NBlocks

</th>
<th valign="top">

RlvLog

Pages

</th>
<th valign="top">

RlvLog

KBytes

</th>
</tr>
<tr>
<td valign="top">

USER1

</td>
<td valign="top">

A1

</td>
<td valign="top">

2

</td>
<td valign="top">

20480

</td>
<td valign="top">

19

</td>
<td valign="top">

19

</td>
<td valign="top">

16

</td>
<td valign="top">

80

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
</tr>
</table>

