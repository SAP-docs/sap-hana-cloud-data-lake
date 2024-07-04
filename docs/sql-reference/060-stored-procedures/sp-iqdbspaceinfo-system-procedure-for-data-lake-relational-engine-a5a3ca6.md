<!-- loioa5a3ca6f84f21015b8efef1f7e569fe6 -->

# sp\_iqdbspaceinfo System Procedure for Data Lake Relational Engine

Displays the size of each object and subobject used in the specified table.



<a name="loioa5a3ca6f84f21015b8efef1f7e569fe6__section_pcl_wvh_b4b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqdbspaceinfo [ <dbspace-name> [, <owner_name>
   [, <object_name> [, <object-type> ] ] ] ]
```



<a name="loioa5a3ca6f84f21015b8efef1f7e569fe6__iq_refbb_1513"/>

## Parameters


<dl>
<dt><b>

*<dbspace-name\>*

</b></dt>
<dd>

\(Optional\) If specified, sp\_iqdbspaceinfo displays one line for each table that has any component in the specified dbspace. Otherwise, the procedure shows information for all dbspaces in the database.



</dd><dt><b>

*<owner\_name\>*

</b></dt>
<dd>

\(Optional\) Owner of the object. If specified, sp\_iqdbspaceinfo displays output only for tables with the specified owner. If not specified, sp\_iqdbspaceinfo displays information on tables for all users in the database.



</dd><dt><b>

*<object\_name\>*

</b></dt>
<dd>

\(Optional\) Name of the table. If not specified, sp\_iqdbspaceinfo displays information on all tables in the database.



</dd><dt><b>

*<object\_type\>*

</b></dt>
<dd>

\(Optional\) Valid table objects.



</dd>
</dl>



<a name="loioa5a3ca6f84f21015b8efef1f7e569fe6__section_d5y_dqz_mbb"/>

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

dbspace\_name

</td>
<td valign="top">

The name of the dbspace.

</td>
</tr>
<tr>
<td valign="top">

object\_type

</td>
<td valign="top">

The type of the object \(table or joinindex only\).

</td>
</tr>
<tr>
<td valign="top">

owner

</td>
<td valign="top">

The name of the owner of the object.

</td>
</tr>
<tr>
<td valign="top">

object\_name

</td>
<td valign="top">

The name of the object on the dbspace.

</td>
</tr>
<tr>
<td valign="top">

object\_id

</td>
<td valign="top">

The global object ID of the object.

</td>
</tr>
<tr>
<td valign="top">

id

</td>
<td valign="top">

The table ID of the bject

</td>
</tr>
<tr>
<td valign="top">

columns

</td>
<td valign="top">

The size of column storage space on the given dbspace.

</td>
</tr>
<tr>
<td valign="top">

indexes

</td>
<td valign="top">

The size of index storage space on the given dbspace. Does not use system-generated indexes \(for example, HG indexes in unique constraints or FP indexes\).

</td>
</tr>
<tr>
<td valign="top">

metadata

</td>
<td valign="top">

The size of storage space for metadata objects on the given dbspace.

</td>
</tr>
<tr>
<td valign="top">

primary\_key

</td>
<td valign="top">

The size of storage space for primary key related objects on the given dbspace.

</td>
</tr>
<tr>
<td valign="top">

unique\_constraint

</td>
<td valign="top">

The size of storage space for unique constraint-related objects on the given dbspace.

</td>
</tr>
<tr>
<td valign="top">

foreign\_key

</td>
<td valign="top">

The size of storage space for foreign-key-related objects on the given dbspace.

</td>
</tr>
<tr>
<td valign="top">

dbspace\_online

</td>
<td valign="top">

Indicates if the dbspace is online \(Y\) or offline \(N\).

</td>
</tr>
<tr>
<td valign="top">

is\_dbspace\_preallocate

</td>
<td valign="top">

"F" indicates that the NOPREALLOCATE keyword was used in the CREATE DBSPACE statement when creating the dbspace on a cooked \(not raw\) filesystem; otherwise "T" \(the default\).

</td>
</tr>
</table>



<a name="loioa5a3ca6f84f21015b8efef1f7e569fe6__iq_refbb_1515"/>

## Remarks

All parameters are optional, and any parameter may be supplied independent of another parameter’s value.

The sp\_iqdbspaceinfo stored procedure supports wildcard characters for interpreting *<dbspace\_name\>*, *<object\_name\>*, and *<owner\_name\>*. It shows information for all dbspaces that match the given pattern in the same way the LIKE clause matches patterns inside queries.

sp\_iqdbspaceinfo shows the DBA the amount of space used by objects that reside on each dbspace. The DBA can use this information to determine which objects must be relocated before a dbspace can be dropped. The subobject columns display sizes reported in integer quantities followed by the suffix B, K, M, G, T, or P, representing bytes, kilobytes, megabytes, gigabytes, terabytes, and petabytes, respectively.

For tables, sp\_iqdbspaceinfo displays subobject sizing information for all subobjects \(using integer quantities with the suffix B, K, M, G, T, or P\) sorted by *<dbspace\_name\>*, *<object\_name\>*, and *<owner\_name\>*.

If you run sp\_iqdbspaceinfo against a server you have started with the -r switch \(read-only\), you see the following error:

```
Msg 13768, Level 14, State 0: SAP SQL Anywhere 
Error -757: Modifications not permitted for read-only database.
```

This behavior is expected. The error does not occur on other stored procedures such as sp\_iqdbspace, sp\_iqfile, sp\_iqdbspaceobjectinfo, or sp\_iqobjectinfo.



<a name="loioa5a3ca6f84f21015b8efef1f7e569fe6__iq_refbb_1512"/>

## Privileges

Requires EXECUTE object-level privilege on this procedure.



## Side Effects

None.



<a name="loioa5a3ca6f84f21015b8efef1f7e569fe6__iq_refbb_1518"/>

## Examples

This example returns the size of all objects and subobjects in all tables in all dbspaces:

```
CALL sp_iqdbspaceinfo;
```


<table>
<tr>
<th valign="top">

dbspace\_name

</th>
<th valign="top">

object\_

type

</th>
<th valign="top">

owner

</th>
<th valign="top">

object\_name

</th>
<th valign="top">

object\_

id

</th>
<th valign="top">

id

</th>
<th valign="top">

columns

</th>
<th valign="top">

primary\_

key

</th>
<th valign="top">

unique\_

constraint

</th>
<th valign="top">

foreign\_

key

</th>
<th valign="top">

dbspace\_

online

</th>
<th valign="top">

is\_dbspace\_

preallocate

</th>
</tr>
<tr>
<td valign="top">

hotsql\_dbspace

</td>
<td valign="top">

table

</td>
<td valign="top">

dbo

</td>
<td valign="top">

iq\_dummy

</td>
<td valign="top">

5763

</td>
<td valign="top">

1726

</td>
<td valign="top">

192K

</td>
<td valign="top">

0B

</td>
<td valign="top">

0B

</td>
<td valign="top">

0B

</td>
<td valign="top">

Y

</td>
<td valign="top">

T

</td>
</tr>
<tr>
<td valign="top">

user\_object\_store

</td>
<td valign="top">

table

</td>
<td valign="top">

HDLADMIN

</td>
<td valign="top">

C1

</td>
<td valign="top">

24369

</td>
<td valign="top">

1857

</td>
<td valign="top">

849K

</td>
<td valign="top">

0B

</td>
<td valign="top">

0B

</td>
<td valign="top">

0B

</td>
<td valign="top">

Y

</td>
<td valign="top">

T

</td>
</tr>
<tr>
<td valign="top">

user\_object\_store

</td>
<td valign="top">

table

</td>
<td valign="top">

HDLADMIN

</td>
<td valign="top">

C2

</td>
<td valign="top">

24372

</td>
<td valign="top">

1858

</td>
<td valign="top">

849K

</td>
<td valign="top">

0B

</td>
<td valign="top">

0B

</td>
<td valign="top">

0B

</td>
<td valign="top">

Y

</td>
<td valign="top">

T

</td>
</tr>
<tr>
<td valign="top">

user\_object\_store

</td>
<td valign="top">

table

</td>
<td valign="top">

HDLADMIN

</td>
<td valign="top">

CUSTOMERS

</td>
<td valign="top">

24442

</td>
<td valign="top">

1873

</td>
<td valign="top">

0B

</td>
<td valign="top">

0B

</td>
<td valign="top">

0B

</td>
<td valign="top">

0B

</td>
<td valign="top">

Y

</td>
<td valign="top">

T

</td>
</tr>
<tr>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
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
<td valign="top">

...

</td>
</tr>
</table>

This example returns the size of all objects and subobjects owned by a specified user in a specified dbspace:

```
CALL sp_iqdbspaceinfo ('user_object_store', ;USER1');
```


<table>
<tr>
<th valign="top">

dbspace\_name

</th>
<th valign="top">

object\_

type

</th>
<th valign="top">

owner

</th>
<th valign="top">

object\_name

</th>
<th valign="top">

object\_

id

</th>
<th valign="top">

id

</th>
<th valign="top">

columns

</th>
<th valign="top">

primary\_

key

</th>
<th valign="top">

unique\_

constraint

</th>
<th valign="top">

foreign\_

key

</th>
<th valign="top">

dbspace\_

online

</th>
<th valign="top">

dbspace\_name

</th>
<th valign="top">

object\_

type

</th>
<th valign="top">

is\_dbspace\_

preallocate

</th>
</tr>
<tr>
<td valign="top">

user\_object\_store

</td>
<td valign="top">

table

</td>
<td valign="top">

USER1

</td>
<td valign="top">

Contacts

</td>
<td valign="top">

3538

</td>
<td valign="top">

732

</td>
<td valign="top">

288K

</td>
<td valign="top">

0B

</td>
<td valign="top">

5.45M

</td>
<td valign="top">

24K

</td>
<td valign="top">

0B

</td>
<td valign="top">

48K

</td>
<td valign="top">

T

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

user\_object\_store

</td>
<td valign="top">

table

</td>
<td valign="top">

USER1

</td>
<td valign="top">

Customers

</td>
<td valign="top">

3515

</td>
<td valign="top">

731

</td>
<td valign="top">

240K

</td>
<td valign="top">

48K

</td>
<td valign="top">

4.63M

</td>
<td valign="top">

24K

</td>
<td valign="top">

0B

</td>
<td valign="top">

0B

</td>
<td valign="top">

T

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

user\_object\_store

</td>
<td valign="top">

table

</td>
<td valign="top">

USER1

</td>
<td valign="top">

Departments

</td>
<td valign="top">

3632

</td>
<td valign="top">

738

</td>
<td valign="top">

72K

</td>
<td valign="top">

0B

</td>
<td valign="top">

1.78M

</td>
<td valign="top">

24K

</td>
<td valign="top">

0B

</td>
<td valign="top">

48K

</td>
<td valign="top">

T

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

user\_object\_store

</td>
<td valign="top">

table

</td>
<td valign="top">

USER1

</td>
<td valign="top">

Employees

</td>
<td valign="top">

3641

</td>
<td valign="top">

739

</td>
<td valign="top">

408K

</td>
<td valign="top">

0B

</td>
<td valign="top">

8.03M

</td>
<td valign="top">

24K

</td>
<td valign="top">

0B

</td>
<td valign="top">

48K

</td>
<td valign="top">

T

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

...

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

...

</td>
<td valign="top">

 

</td>
</tr>
</table>

**Related Information**  


[sp\_iqindexinfo System Procedure for Data Lake Relational Engine](sp-iqindexinfo-system-procedure-for-data-lake-relational-engine-a5ac909.md "Displays the number of blocks (objects) used per index per main dbspace for a given object. If the object resides on several dbspaces, sp_iqindexinfo returns the space used in all dbspaces, as shown in the example.")

[sp\_iqdbspace System Procedure for Data Lake Relational Engine](sp-iqdbspace-system-procedure-for-data-lake-relational-engine-a5a34b5.md "Displays detailed information about each data lake Relational Engine dbspace.")

[sp\_iqspaceinfo System Procedure for Data Lake Relational Engine](sp-iqspaceinfo-system-procedure-for-data-lake-relational-engine-a5b6d30.md "Displays the number of blocks (objects) used by each object in the current database and the name of the dbspace in which the object is located.")

