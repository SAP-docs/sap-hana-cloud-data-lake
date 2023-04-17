<!-- loioa5ba627c84f2101591d9cedf0830a4e0 -->

# sp\_iqtablesize Procedure for Data Lake Relational Engine

Returns the size of the specified table.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqtablesize ( <table_owner>.<table_name> )
```



<a name="loioa5ba627c84f2101591d9cedf0830a4e0__sp_iqtablesize_parm1"/>

## Parameters

 *<table\_owner\>*
 :   The owner of the table.

  *<table\_name\>*
 :   The name of the table.

 

<a name="loioa5ba627c84f2101591d9cedf0830a4e0__sp_iqtablesize_returns1"/>

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

The physical table size, in kilobytes. If you divide the KBytes value by page size, you see the average on-disk page size.



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

The number of data lake Relational Engine blocks. NBlocks is Kbytes divided by block size. Each data lake Relational Engine page on disk uses 1 to 16 blocks. If the page size is 128 KB, then the block size is 8 KB. In this case, an individual on-disk page could be 8, 16, 24, 32, 40, 48, 56, 64, 72, 80, 88, 96, 104, 112, 120, or 128 KB.



</td>
</tr>
</table>



<a name="loioa5ba627c84f2101591d9cedf0830a4e0__sp_iqtablesize_remarks1"/>

## Remarks

Returns the total size of the table in KBytes and NBlocks \(data lake Relational Engine blocks\). Also returns the number of pages required to hold the table in memory, and the number of data lake Relational Engine pages that are compressed when the table is compressed \(on disk\). You need to specify the *<table\_name\>* parameter with this procedure. If you are the owner of *<table\_name\>*, then you do not have to specify the *<table\_owner\>* parameter.

> ### Note:  
> Data lake Relational Engine always reads and writes an entire page, not blocks. For example, if an individual page compresses to 88 KB, then data lake Relational Engine reads and writes the 88 KB in one I/O. The average page is compressed by a factor of 2 to 3.



<a name="loioa5ba627c84f2101591d9cedf0830a4e0__iq_refbb_1807"/>

## Privileges

To run this procedure, you need the EXECUTE privilege on the procedure. See [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md). 

You also need one of the following:


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

-   MANAGE ANY DBSPACE
-   ALTER ANY TABLE
-   You own the table



</td>
<td valign="top">

System privileges



</td>
<td valign="top">

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md)



</td>
</tr>
</table>



<a name="loioa5ba627c84f2101591d9cedf0830a4e0__sp_iqtablesize_sideeffects1"/>

## Side Effects

None



<a name="loioa5ba627c84f2101591d9cedf0830a4e0__sp_iqtablesize_example1"/>

## Example

```
call sp_iqtablesize ('dba.t1')
```


<table>
<tr>
<th valign="top" rowspan="1">

Ownername



</th>
<th valign="top" rowspan="1">

Tablename



</th>
<th valign="top" rowspan="1">

Columns



</th>
</tr>
<tr>
<td valign="top" rowspan="1">

DBA



</td>
<td valign="top" rowspan="1">

t1



</td>
<td valign="top" rowspan="1">

3



</td>
</tr>
</table>


<table>
<tr>
<th valign="top" rowspan="1">

\(Continued\)

KBytes



</th>
<th valign="top" rowspan="1">

Pages



</th>
<th valign="top" rowspan="1">

CompressedPages



</th>
</tr>
<tr>
<td valign="top" rowspan="1">

192



</td>
<td valign="top" rowspan="1">

5



</td>
<td valign="top" rowspan="1">

4



</td>
</tr>
</table>


<table>
<tr>
<th valign="top" rowspan="1">

\(Continued\)

NBlocs



</th>
</tr>
<tr>
<td valign="top" rowspan="1">

24



</td>
</tr>
</table>


<table>
</table>

