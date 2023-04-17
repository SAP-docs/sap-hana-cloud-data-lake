<!-- loioa5ad8fe784f21015bda0e710013b6646 -->

# sp\_iqindexsize Procedure for Data Lake Relational Engine

Gives the size of the specified index.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqindexsize [ [ <owner>.]<table_name>.]<index_name> 
```



<a name="loioa5ad8fe784f21015bda0e710013b6646__sp_iqindexsize_parm1"/>

## Parameters

 *<owner\>*
 :   The owner of the table.

  *<table\_name\>*
 :   The name of the table.

  *<index\_name\>*
 :   The name of the index.

 

<a name="loioa5ad8fe784f21015bda0e710013b6646__sp_iqindexsize_returns1"/>

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

`Username`



</td>
<td valign="top">

Index owner.



</td>
</tr>
<tr>
<td valign="top">

`Indexname`



</td>
<td valign="top">

Index for which results are returned, including the table name.



</td>
</tr>
<tr>
<td valign="top">

`Type`



</td>
<td valign="top">

Index type.



</td>
</tr>
<tr>
<td valign="top">

`Info`



</td>
<td valign="top">

Component of the data lake Relational Engine index for which the KBytes, Pages, and Compressed Pages are being reported. The components vary by index type. For example, the default \(FP\) index includes BARRAY \(barray\) and Bitmap \(bm\) components.



</td>
</tr>
<tr>
<td valign="top">

`KBytes`



</td>
<td valign="top">

Physical object size in KB.



</td>
</tr>
<tr>
<td valign="top">

`Pages`



</td>
<td valign="top">

Number of data lake Relational Engine pages needed to hold the object in memory.



</td>
</tr>
<tr>
<td valign="top">

`Compressed Pages`



</td>
<td valign="top">

Number of data lake Relational Engine pages when the object is compressed \(on disk\).



</td>
</tr>
</table>



<a name="loioa5ad8fe784f21015bda0e710013b6646__sp_iqindexsize_remarks1"/>

## Remarks

Returns the total size of the index in bytes and kilobytes, and an Info column that describes the component of the data lake Relational Engine index for which the KBytes, Pages, and Compressed Pages are reported. The components described vary by index type. For example, the default \(FP\) index includes BARRAY \(barray\) and Bitmap \(bm\) components.

Also returns the number of pages required to hold the object in memory and the number of data lake Relational Engine pages when the index is compressed \(on disk\).

You must specify the *<index\_name\>* parameter with this procedure. To restrict results to this index name in a single table, include *<owner.table.\>* when specifying the index.



<a name="loioa5ad8fe784f21015bda0e710013b6646__iq_refbb_1619"/>

## Privileges

To run this procedure, you need the EXECUTE privilege on the procedure. See [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md). If you own the object referenced by the procedure, no additional privilege is required.

For objects owned by others, you need one of the following privileges:


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

-   ALTER ANY TABLE
-   ALTER ANY INDEX



</td>
<td valign="top">

System privileges



</td>
<td valign="top">

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md)



</td>
</tr>
</table>



<a name="loioa5ad8fe784f21015bda0e710013b6646__sp_iqindexsize_sideeffects1"/>

## Side Effects

None



<a name="loioa5ad8fe784f21015bda0e710013b6646__sp_iqindexsize_examples1"/>

## Example

```
sp_iqindexsize ASIQ_IDX_T780_I4_HG
```


<table>
<tr>
<th valign="top">

Username



</th>
<th valign="top">

Indexname



</th>
<th valign="top">

Type



</th>
<th valign="top">

Info



</th>
<th valign="top">

Kbytes



</th>
<th valign="top">

Pages



</th>
<th valign="top">

Compressed Pages



</th>
</tr>
<tr>
<td valign="top">

GROUPO



</td>
<td valign="top">

GROUPO.Departments.ASIQ\_IDX\_T780\_I4\_HG



</td>
<td valign="top">

HG



</td>
<td valign="top">

Total



</td>
<td valign="top">

288



</td>
<td valign="top">

4



</td>
<td valign="top">

2



</td>
</tr>
<tr>
<td valign="top">

GROUPO



</td>
<td valign="top">

GROUPO.Departments.ASIQ\_IDX\_T780\_I4\_HG



</td>
<td valign="top">

HG



</td>
<td valign="top">

vdo



</td>
<td valign="top">

0



</td>
<td valign="top">

0



</td>
<td valign="top">

0



</td>
</tr>
<tr>
<td valign="top">

GROUPO



</td>
<td valign="top">

GROUPO.Departments.ASIQ\_IDX\_T780\_I4\_HG



</td>
<td valign="top">

HG



</td>
<td valign="top">

bt



</td>
<td valign="top">

152



</td>
<td valign="top">

2



</td>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top">

GROUPO



</td>
<td valign="top">

GROUPO.Departments.ASIQ\_IDX\_T780\_I4\_HG



</td>
<td valign="top">

HG



</td>
<td valign="top">

garray



</td>
<td valign="top">

0



</td>
<td valign="top">

0



</td>
<td valign="top">

0



</td>
</tr>
<tr>
<td valign="top">

GROUPO



</td>
<td valign="top">

GROUPO.Departments.ASIQ\_IDX\_T780\_I4\_HG



</td>
<td valign="top">

HG



</td>
<td valign="top">

bm



</td>
<td valign="top">

136



</td>
<td valign="top">

2



</td>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top">

GROUPO



</td>
<td valign="top">

GROUPO.Departments.ASIQ\_IDX\_T780\_I4\_HG



</td>
<td valign="top">

HG



</td>
<td valign="top">

barray



</td>
<td valign="top">

0



</td>
<td valign="top">

0



</td>
<td valign="top">

0



</td>
</tr>
<tr>
<td valign="top">

GROUPO



</td>
<td valign="top">

GROUPO.Departments.ASIQ\_IDX\_T780\_I4\_HG



</td>
<td valign="top">

HG



</td>
<td valign="top">

dpstore



</td>
<td valign="top">

0



</td>
<td valign="top">

0



</td>
<td valign="top">

0



</td>
</tr>
<tr>
<td valign="top">

GROUPO



</td>
<td valign="top">

GROUPO.Departments.ASIQ\_IDX\_T780\_I4\_HG



</td>
<td valign="top">

HG



</td>
<td valign="top">

largelob



</td>
<td valign="top">

0



</td>
<td valign="top">

0



</td>
<td valign="top">

0



</td>
</tr>
<tr>
<td valign="top">

GROUPO



</td>
<td valign="top">

GROUPO.Departments.ASIQ\_IDX\_T780\_I4\_HG



</td>
<td valign="top">

HG



</td>
<td valign="top">

txtPst



</td>
<td valign="top">

0



</td>
<td valign="top">

0



</td>
<td valign="top">

0



</td>
</tr>
</table>

```
CREATE TEXT INDEX ti ON Employees( Street ) IMMEDIATE REFRESH;sp_iqindexsize 'ti';
```


<table>
<tr>
<th valign="top">

Username



</th>
<th valign="top">

Indexname



</th>
<th valign="top">

Type



</th>
<th valign="top">

Info



</th>
<th valign="top">

KBytes



</th>
<th valign="top">

Pages



</th>
<th valign="top">

Compressed Pages



</th>
</tr>
<tr>
<td valign="top">

GROUPO



</td>
<td valign="top">

GROUPO.Employees.ti



</td>
<td valign="top">

TEXT



</td>
<td valign="top">

Total



</td>
<td valign="top">

896



</td>
<td valign="top">

12



</td>
<td valign="top">

6



</td>
</tr>
<tr>
<td valign="top">

GROUPO



</td>
<td valign="top">

GROUPO.Employees.ti



</td>
<td valign="top">

TEXT



</td>
<td valign="top">

vdo



</td>
<td valign="top">

0



</td>
<td valign="top">

0



</td>
<td valign="top">

0



</td>
</tr>
<tr>
<td valign="top">

GROUPO



</td>
<td valign="top">

GROUPO.Employees.ti



</td>
<td valign="top">

TEXT



</td>
<td valign="top">

bt



</td>
<td valign="top">

304



</td>
<td valign="top">

4



</td>
<td valign="top">

2



</td>
</tr>
<tr>
<td valign="top">

GROUPO



</td>
<td valign="top">

GROUPO.Employees.ti



</td>
<td valign="top">

TEXT



</td>
<td valign="top">

garray



</td>
<td valign="top">

152



</td>
<td valign="top">

2



</td>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top">

GROUPO



</td>
<td valign="top">

GROUPO.Employees.ti



</td>
<td valign="top">

TEXT



</td>
<td valign="top">

bm



</td>
<td valign="top">

136



</td>
<td valign="top">

2



</td>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top">

GROUPO



</td>
<td valign="top">

GROUPO.Employees.ti



</td>
<td valign="top">

TEXT



</td>
<td valign="top">

barray



</td>
<td valign="top">

152



</td>
<td valign="top">

2



</td>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top">

GROUPO



</td>
<td valign="top">

GROUPO.Employees.ti



</td>
<td valign="top">

TEXT



</td>
<td valign="top">

dpstore



</td>
<td valign="top">

0



</td>
<td valign="top">

0



</td>
<td valign="top">

0



</td>
</tr>
<tr>
<td valign="top">

GROUPO



</td>
<td valign="top">

GROUPO.Employees.ti



</td>
<td valign="top">

TEXT



</td>
<td valign="top">

largelob



</td>
<td valign="top">

0



</td>
<td valign="top">

0



</td>
<td valign="top">

0



</td>
</tr>
<tr>
<td valign="top">

GROUPO



</td>
<td valign="top">

GROUPO.Employees.ti



</td>
<td valign="top">

TEXT



</td>
<td valign="top">

txtPst



</td>
<td valign="top">

304



</td>
<td valign="top">

4



</td>
<td valign="top">

2



</td>
</tr>
</table>

**Related Information**  


[sp\_iqindexmetadata Procedure for Data Lake Relational Engine](sp-iqindexmetadata-procedure-for-data-lake-relational-engine-a5ad0e4.md "Displays index metadata for a given index.")

[sp\_iqindexfragmentation Procedure for Data Lake Relational Engine](sp-iqindexfragmentation-procedure-for-data-lake-relational-engine-a5ac10a.md "Reports information about the percentage of page space taken up within the B-trees, garrays, and bitmap structures in data lake Relational Engine indexes.")

[sp\_iqindexinfo Procedure for Data Lake Relational Engine](sp-iqindexinfo-procedure-for-data-lake-relational-engine-a5ac909.md "Displays the number of blocks (objects) used per index per main dbspace for a given object. If the object resides on several dbspaces, sp_iqindexinfo returns the space used in all dbspaces, as shown in the example.")

