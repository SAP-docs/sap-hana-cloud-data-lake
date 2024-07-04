<!-- loioa5b6d30884f21015b460b72ef2bc8109 -->

# sp\_iqspaceinfo System Procedure for Data Lake Relational Engine

Displays the number of blocks\(objects\) used by each object in the current database and the name of the dbspace in which the object is located.



<a name="loioa5b6d30884f21015b460b72ef2bc8109__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqspaceinfo ['main | [table <table-name> | index <index-name>] [...] ']
```



<a name="loioa5b6d30884f21015b460b72ef2bc8109__iq_refbb_1759"/>

## Parameters


<dl>
<dt><b>

*<table-name\>*

</b></dt>
<dd>

The name of the table.



</dd><dt><b>

*<index-name\>*

</b></dt>
<dd>

The name of the index.



</dd>
</dl>



<a name="loioa5b6d30884f21015b460b72ef2bc8109__section_zzs_mnz_kbc"/>

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

Name

</td>
<td valign="top">

The object name

</td>
</tr>
<tr>
<td valign="top">

NBlocks

</td>
<td valign="top">

The snumber of blocks \(or objects, in instances using cloud dbspaces\) used by each object.

</td>
</tr>
<tr>
<td valign="top">

dbspace\_name

</td>
<td valign="top">

Displays the name of the dbspace.

</td>
</tr>
</table>



<a name="loioa5b6d30884f21015b460b72ef2bc8109__iq_refbb_1761"/>

## Remarks

For the current database, displays the object name, number of objects, and the name of the dbspace. sp\_iqspaceinfo requires no parameters.

The information returned by sp\_iqspaceinfo is helpful in managing dbspaces.

The default parameter is main, which returns the size of the shared data lake Relational Engine store.

If you supply no parameter, you need to have at least one user-created object, such as a table, to receive results.



<a name="loioa5b6d30884f21015b460b72ef2bc8109__iq_refbb_1760"/>

## Privileges

Requires all of the following:

-   EXECUTE object-level privilege on this procedure
-   MANAGE ANY DBSPACE system privilege



## Side Effects

None.



<a name="loioa5b6d30884f21015b460b72ef2bc8109__iq_refbb_1762"/>

## Examples

This example returns the number of blocks used by each object in the database.

```
CALL sp_iqspaceinfo
```


<table>
<tr>
<th valign="top">

Name

</th>
<th valign="top">

NBlocks

</th>
<th valign="top">

dbspace\_name

</th>
</tr>
<tr>
<td valign="top">

Contacts

</td>
<td valign="top">

19

</td>
<td valign="top">

user\_object\_store

</td>
</tr>
<tr>
<td valign="top">

SalesOrderItems.DBA.ASIQ\_IDX\_T205\_C5\_FP

</td>
<td valign="top">

56

</td>
<td valign="top">

user\_object\_store

</td>
</tr>
<tr>
<td valign="top">

Contacts.DBA.ASIQ\_IDX\_T206\_C10\_FP

</td>
<td valign="top">

55

</td>
<td valign="top">

user\_object\_store

</td>
</tr>
<tr>
<td valign="top">

Customers

</td>
<td valign="top">

20

</td>
<td valign="top">

user\_object\_store

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

...

</td>
</tr>
</table>

This example returns information for table A1 owned by USER2:

```
CALL sp_iqspaceinfo ('table USER2.A1')
```


<table>
<tr>
<th valign="top">

Name

</th>
<th valign="top">

NBlocks

</th>
<th valign="top">

dbspace\_name

</th>
</tr>
<tr>
<td valign="top">

USER1.A1

</td>
<td valign="top">

24

</td>
<td valign="top">

user\_object\_store

</td>
</tr>
</table>

**Related Information**  


[sp\_iqindexinfo System Procedure for Data Lake Relational Engine](sp-iqindexinfo-system-procedure-for-data-lake-relational-engine-a5ac909.md "Displays the number of blocks (objects) used per index per main dbspace for a given object. If the object resides on several dbspaces, sp_iqindexinfo returns the space used in all dbspaces, as shown in the example.")

[sp\_iqdbspace System Procedure for Data Lake Relational Engine](sp-iqdbspace-system-procedure-for-data-lake-relational-engine-a5a34b5.md "Displays detailed information about each data lake Relational Engine dbspace.")

[sp\_iqdbspaceinfo System Procedure for Data Lake Relational Engine](sp-iqdbspaceinfo-system-procedure-for-data-lake-relational-engine-a5a3ca6.md "Displays the size of each object and subobject used in the specified table.")

