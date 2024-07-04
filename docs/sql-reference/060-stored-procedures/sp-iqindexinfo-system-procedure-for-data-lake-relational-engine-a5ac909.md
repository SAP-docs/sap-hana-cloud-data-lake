<!-- loioa5ac909e84f210158be2ec9a4fd2e670 -->

# sp\_iqindexinfo System Procedure for Data Lake Relational Engine

Displays the number of blocks\(objects\) used per index per main dbspace for a given object. If the object resides on several dbspaces, sp\_iqindexinfo returns the space used in all dbspaces, as shown in the example.



<a name="loioa5ac909e84f210158be2ec9a4fd2e670__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqindexinfo ('
   { DATABASE 
   | table <table-name> 
   | index <index-name> [...] }
   [ resources <resource-percent> ]
   ')
```



<a name="loioa5ac909e84f210158be2ec9a4fd2e670__section_zhr_yv2_pbb"/>

## Parameters


<dl>
<dt><b>

*<table-name\>*

</b></dt>
<dd>

The name of the table.



</dd>
</dl>


<dl>
<dt><b>

*<index-name\>*

</b></dt>
<dd>

The name of the index.



</dd>
</dl>


<dl>
<dt><b>

*<resource-percent\>*

</b></dt>
<dd>

The resources percentage allows you to limit the CPU utilization of the sp\_iqindexinfo procedure by specifying the percent of total CPUs to use. *<resource-percent\>* must be an integer greater than 0.



</dd>
</dl>



<a name="loioa5ac909e84f210158be2ec9a4fd2e670__section_xvl_gcz_mbb"/>

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

The minimum object ID.

</td>
</tr>
<tr>
<td valign="top">

MaxBlk

</td>
<td valign="top">

The maximum object ID.

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

Requires all of the following:

-   EXECUTE object-level privilege on this procedure
-   MANAGE ANY DBSPACE system privilege



## Side Effects

None.



<a name="loioa5ac909e84f210158be2ec9a4fd2e670__iq_refbb_1611"/>

## Examples

This example returns information on the dbspaces a given object resides in, along with information about indexes in the Departments table:

```
CALL sp_iqindexinfo ('TABLE USER1.Departments');
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

USER1.Departments

</td>
<td valign="top">

user\_object\_store

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

USER1.Departments.ASIQ\_IDX\_T779\_C1\_FP

</td>
<td valign="top">

user\_object\_store

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

USER1.Departments.ASIQ\_IDX\_T779\_C2\_FP

</td>
<td valign="top">

user\_object\_store

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

USER1.Departments.ASIQ\_IDX\_T779\_C3\_FP

</td>
<td valign="top">

user\_object\_store

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

USER1.Departments.ASIQ\_IDX\_T779\_C3\_HG

</td>
<td valign="top">

user\_object\_store

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

USER1.Departments.ASIQ\_IDX\_T779\_I4\_HG

</td>
<td valign="top">

user\_object\_store

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


[sp\_iqdbspace System Procedure for Data Lake Relational Engine](sp-iqdbspace-system-procedure-for-data-lake-relational-engine-a5a34b5.md "Displays detailed information about each data lake Relational Engine dbspace.")

[sp\_iqdbspaceinfo System Procedure for Data Lake Relational Engine](sp-iqdbspaceinfo-system-procedure-for-data-lake-relational-engine-a5a3ca6.md "Displays the size of each object and subobject used in the specified table.")

[sp\_iqspaceinfo System Procedure for Data Lake Relational Engine](sp-iqspaceinfo-system-procedure-for-data-lake-relational-engine-a5b6d30.md "Displays the number of blocks (objects) used by each object in the current database and the name of the dbspace in which the object is located.")

[sp\_iqindexmetadata System Procedure for Data Lake Relational Engine](sp-iqindexmetadata-system-procedure-for-data-lake-relational-engine-a5ad0e4.md "Displays index metadata for a given index.")

[sp\_iqindexfragmentation System Procedure for Data Lake Relational Engine](sp-iqindexfragmentation-system-procedure-for-data-lake-relational-engine-a5ac10a.md "Reports information about the percentage of page space taken up within the B-trees, garrays, and bitmap structures in data lake Relational Engine indexes.")

[sp\_iqindexsize System Procedure for Data Lake Relational Engine](sp-iqindexsize-system-procedure-for-data-lake-relational-engine-a5ad8fe.md "Gives the size of the specified index.")

