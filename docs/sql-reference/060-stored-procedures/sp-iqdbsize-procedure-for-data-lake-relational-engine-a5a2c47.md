<!-- loioa5a2c47f84f21015ae93aa3096658803 -->

# sp\_iqdbsize Procedure for Data Lake Relational Engine

Displays the size of the current database.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqdbsize ( [ main ] )
```



<a name="loioa5a2c47f84f21015ae93aa3096658803__iq_refbb_1501"/>

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

Database



</td>
<td valign="top">

The path name of the database file.



</td>
</tr>
<tr>
<td valign="top">

PhysicalBlocks



</td>
<td valign="top">

The total database size in blocks. A data lake Relational Engine database consists of one or more dbspaces. Each dbspace has a fixed size, which is originally specified in units of megabytes. This megabyte quantity is converted to blocks using the data lake Relational Engine page size and the corresponding block size for that data lake Relational Engine page size. The Physical Blocks column reflects the cumulative total of each data lake Relational Engine dbspace size, represented in blocks.



</td>
</tr>
<tr>
<td valign="top">

KBytes



</td>
<td valign="top">

The total size of the database, in kilobytes. This value is the total size of the database in blocks \(PhysicalBlocks in the previous sp\_iqdbsize column\) multiplied by the block size. The block size depends on the data lake Relational Engine page size.



</td>
</tr>
<tr>
<td valign="top">

Pages



</td>
<td valign="top">

The total number of data lake Relational Engine pages necessary to represent in memory all of the data stored in tables and the metadata for these objects. This value is always greater than or equal to the value of CompressedPages \(the next sp\_iqdbsize column\).



</td>
</tr>
<tr>
<td valign="top">

CompressedPages



</td>
<td valign="top">

The total number of data lake Relational Engine pages necessary to store on disk the data in tables and metadata for these objects. This value is always less than or equal to the value of Pages \(the previous sp\_iqdbsize column\), because data lake Relational Engine compresses pages when the data lake Relational Engine page is written from memory to disk. The sp\_iqdbsize CompressedPages column represents the number of compressed pages.



</td>
</tr>
<tr>
<td valign="top">

NBlocks



</td>
<td valign="top">

The total size in blocks used to store the data in tables. This value is always less than or equal to the sp\_iqdbsize PhysicalBlocks value.



</td>
</tr>
<tr>
<td valign="top">

CatalogBlocks



</td>
<td valign="top">

The total size in blocks used to store the metadata for tables.



</td>
</tr>
</table>



<a name="loioa5a2c47f84f21015ae93aa3096658803__iq_refbb_1503"/>

## Remarks

Returns the total size of the database. Also returns the number of pages required to hold the database in memory and the number of data lake Relational Engine pages when the database is compressed \(on disk\).

If run on a multiplex database, the default parameter is main, which returns the size of the shared data lake Relational Engine store.



<a name="loioa5a2c47f84f21015ae93aa3096658803__iq_refbb_1502"/>

## Privileges

To run this procedure, you need the EXECUTE privilege on the procedure. See [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md). 



## Side Effects

None



<a name="loioa5a2c47f84f21015ae93aa3096658803__iq_refbb_1505"/>

## Example

The following example displays size information for the database iqdemo:

```
sp_iqdbsize
```


<table>
<tr>
<th valign="top">

Database



</th>
<th valign="top">

PhysicalBlocks



</th>
<th valign="top">

KBytes



</th>
<th valign="top">

Pages



</th>
<th valign="top">

CompressedPages



</th>
</tr>
<tr>
<td valign="top">

/data\_local/mpx-writer-0-0/iqaas.db



</td>
<td valign="top">

19786



</td>
<td valign="top">

456



</td>
<td valign="top">

15



</td>
<td valign="top">

13



</td>
</tr>
</table>


<table>
<tr>
<th valign="top">

NBlocks



</th>
<th valign="top">

CatalogBlocks



</th>
</tr>
<tr>
<td valign="top">

57



</td>
<td valign="top">

36



</td>
</tr>
</table>

