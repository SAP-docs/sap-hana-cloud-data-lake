<!-- loioa5ac909e84f210158be2ec9a4fd2e670 -->

# sp\_iqindexinfo Procedure for Data Lake Relational Engine

Displays the number of blocks\(objects\) used per index per main dbspace for a given object. If the object resides on several dbspaces, sp\_iqindexinfo returns the space used in all dbspaces, as shown in the example.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqindexinfo '{ database | [ table <table-name> | index <index-name> ] [...] } 
   [ resources <resource-percent> ]'
```



<a name="loioa5ac909e84f210158be2ec9a4fd2e670__section_zhr_yv2_pbb"/>

## Parameters

 *<table-name\>*
 :   The name of the table.

  *<index-name\>*
 :   The name of the index.

  *<resource-percent\>*
 :   The resources percentage allows you to limit the CPU utilization of the sp\_iqindexinfo procedure by specifying the percent of total CPUs to use. *<resource-percent\>* must be an integer greater than 0.

 

<a name="loioa5ac909e84f210158be2ec9a4fd2e670__section_xvl_gcz_mbb"/>

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

Object



</td>
<td valign="top">

Table or index name.



</td>
</tr>
<tr>
<td valign="top">

Dbspace\_name



</td>
<td valign="top">

Name of the dbspace.



</td>
</tr>
<tr>
<td valign="top">

ObjSize



</td>
<td valign="top">

Size of data for this object on this dbspace.



</td>
</tr>
<tr>
<td valign="top">

DBSpPct



</td>
<td valign="top">

Percent of dbspace used by this object.



</td>
</tr>
<tr>
<td valign="top">

MinBlk



</td>
<td valign="top">

First block used by this object on this dbspace.For instances using cloud dbspaces, this is the minimum object ID.



</td>
</tr>
<tr>
<td valign="top">

MaxBlk



</td>
<td valign="top">

Last block used by this object on this dbspace; useful for determining which objects must be relocated before the dbspace is resized to a smaller size.For instances using cloud dbspaces, this is the maximum object ID.



</td>
</tr>
</table>



<a name="loioa5ac909e84f210158be2ec9a4fd2e670__iq_refbb_1608"/>

## Remarks

You can request index information for the entire database, or you can specify any number of table or index parameters. If a table name is specified, sp\_iqindexinfo returns information on all indexes in the table. If an index name is specified, only the information on that index is returned.

If the specified *<table-name\>* or *<index-name\>* is ambiguous or the object cannot be found, an error is returned.

By default in a multiplex database, sp\_iqindexinfo displays information about the shared data lake Relational Engine store on a worker node. If individual tables or indexes are specified, the store to display is automatically selected.

sp\_iqindexinfo shows the DBA on which dbspaces a given object resides. The DBA can use this information to determine which dbspaces must be given relocate mode to relocate the object.



<a name="loioa5ac909e84f210158be2ec9a4fd2e670__iq_refbb_1607"/>

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

MANAGE ANY DBSPACE



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



<a name="loioa5ac909e84f210158be2ec9a4fd2e670__iq_refbb_1611"/>

## Example

Shows the DBA on which dbspaces a given object resides. Displays information about indexes in the Departments table:

```
sp_iqindexinfo 'table GROUPO.Departments';
```


<table>
<tr>
<th valign="top">

Object



</th>
<th valign="top">

DbspaceName



</th>
<th valign="top">

ObjSize



</th>
<th valign="top">

DBSpPct



</th>
<th valign="top">

MinBlk



</th>
<th valign="top">

MaxBlk



</th>
</tr>
<tr>
<td valign="top">

GROUPO.Departments



</td>
<td valign="top">

iq\_main



</td>
<td valign="top">

288 K



</td>
<td valign="top">

1



</td>
<td valign="top">

1,045,496.00



</td>
<td valign="top">

1,048,891.00



</td>
</tr>
<tr>
<td valign="top">

GROUPO.Departments.ASIQ\_IDX\_T779\_C1\_FP



</td>
<td valign="top">

iq\_main



</td>
<td valign="top">

176 K



</td>
<td valign="top">

1



</td>
<td valign="top">

1,047,197.00



</td>
<td valign="top">

1,047,328.00



</td>
</tr>
<tr>
<td valign="top">

GROUPO.Departments.ASIQ\_IDX\_T779\_C2\_FP



</td>
<td valign="top">

iq\_main



</td>
<td valign="top">

160 K



</td>
<td valign="top">

1



</td>
<td valign="top">

1,047,213.00



</td>
<td valign="top">

1,047,324.00



</td>
</tr>
<tr>
<td valign="top">

GROUPO.Departments.ASIQ\_IDX\_T779\_C3\_FP



</td>
<td valign="top">

iq\_main



</td>
<td valign="top">

184 K



</td>
<td valign="top">

1



</td>
<td valign="top">

1,047,229.00



</td>
<td valign="top">

1,047,317.00



</td>
</tr>
<tr>
<td valign="top">

GROUPO.Departments.ASIQ\_IDX\_T779\_C3\_HG



</td>
<td valign="top">

iq\_main



</td>
<td valign="top">

440 K



</td>
<td valign="top">

1



</td>
<td valign="top">

1,048,421.00



</td>
<td valign="top">

1,048,796.00



</td>
</tr>
<tr>
<td valign="top">

GROUPO.Departments.ASIQ\_IDX\_T779\_I4\_HG



</td>
<td valign="top">

iq\_main



</td>
<td valign="top">

288 K



</td>
<td valign="top">

1



</td>
<td valign="top">

1,047,261.00



</td>
<td valign="top">

1,047,306.00



</td>
</tr>
</table>

**Related Information**  


[sp\_iqdbspace Procedure for Data Lake Relational Engine](sp-iqdbspace-procedure-for-data-lake-relational-engine-a5a34b5.md "Displays detailed information about each data lake Relational Engine dbspace.")

[sp\_iqdbspaceinfo Procedure for Data Lake Relational Engine](sp-iqdbspaceinfo-procedure-for-data-lake-relational-engine-a5a3ca6.md "Displays the size of each object and subobject used in the specified table.")

[sp\_iqspaceinfo Procedure for Data Lake Relational Engine](sp-iqspaceinfo-procedure-for-data-lake-relational-engine-a5b6d30.md "Displays the number of blocks (objects) used by each object in the current database and the name of the dbspace in which the object is located.")

[sp\_iqindexmetadata Procedure for Data Lake Relational Engine](sp-iqindexmetadata-procedure-for-data-lake-relational-engine-a5ad0e4.md "Displays index metadata for a given index.")

[sp\_iqindexfragmentation Procedure for Data Lake Relational Engine](sp-iqindexfragmentation-procedure-for-data-lake-relational-engine-a5ac10a.md "Reports information about the percentage of page space taken up within the B-trees, garrays, and bitmap structures in data lake Relational Engine indexes.")

[sp\_iqindexsize Procedure for Data Lake Relational Engine](sp-iqindexsize-procedure-for-data-lake-relational-engine-a5ad8fe.md "Gives the size of the specified index.")

[Cloud Dbspaces](https://help.sap.com/viewer/a896c6a184f21015b5bcf4c7a967df07/2023_1_QRC/en-US/493eb818429e4996b3da4153192a9efa.html "Cloud dbspace is a new offering where the database engine stores a user dbspace in object storage solutions such as Microsoft Azure Blob Storage, AWS Simple Storage Service (S3), or Google Cloud Storage. In a cloud dbspace, database pages are physically stored as objects as opposed to regular file system blocks.") :arrow_upper_right:

