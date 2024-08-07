<!-- loioa5b0b72884f210158266fa85e5483c9c -->

# sp\_iqobjectinfo System Procedure for Data Lake Relational Engine

Returns partitions and dbspace assignments of database objects and subobjects.



<a name="loioa5b0b72884f210158266fa85e5483c9c__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqobjectinfo [ <owner_name> ]  [ , <object_name> ] [ , <object-type> ] 
```



<a name="loioa5b0b72884f210158266fa85e5483c9c__iq_refbb_1681"/>

## Parameters


<dl>
<dt><b>

*<owner\_name\>*

</b></dt>
<dd>

\(Optional\) Owner of the object. If specified, sp\_iqobjectinfo displays output only for tables with the specified owner. If not specified, sp\_iqobjectinfo displays information on tables for all users in the database.



</dd><dt><b>

*<object\_name\>*

</b></dt>
<dd>

\(Optional\) Name of the table. If not specified, sp\_iqobjectinfo displays information on all tables in the database.



</dd><dt><b>

*<object-type\>*

</b></dt>
<dd>

\(Optional\) Valid `table` object types. If *<object-type\>* is a table, enclose it in quotation marks.



</dd>
</dl>



<a name="loioa5b0b72884f210158266fa85e5483c9c__section_iwy_zlg_nbb"/>

## Result Set

Returns all the partitions and the dbspace assignments of a particular or all database objects \(of type table\) and its subobjects. The subobjects are columns, indexes, primary key, unique constraints, and foreign keys.


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

owner

</td>
<td valign="top">

Name of the owner of the object.

</td>
</tr>
<tr>
<td valign="top">

object\_name

</td>
<td valign="top">

Name of the object \(of type table\) located on the dbspace.

</td>
</tr>
<tr>
<td valign="top">

sub\_object\_name

</td>
<td valign="top">

Name of the object located on the dbspace.

</td>
</tr>
<tr>
<td valign="top">

object\_type

</td>
<td valign="top">

Type of the object \(column, index, primary key, unique constraint, foreign key, partition, or table\).

</td>
</tr>
<tr>
<td valign="top">

object\_id

</td>
<td valign="top">

Global object ID of the object.

</td>
</tr>
<tr>
<td valign="top">

id

</td>
<td valign="top">

Table ID of the object.

</td>
</tr>
<tr>
<td valign="top">

dbspace\_name

</td>
<td valign="top">

Name of the dbspace on which the object resides. The string "\[multiple\]" appears in a special meta row for partitioned objects. The \[multiple\] row indicates that multiple rows follow in the output to describe the table or column.

</td>
</tr>
<tr>
<td valign="top">

partition\_name

</td>
<td valign="top">

Name of the partition for the given object.

</td>
</tr>
</table>



<a name="loioa5b0b72884f210158266fa85e5483c9c__section_mj4_bmg_nbb"/>

## Remarks

All parameters are optional, and any parameter may be supplied independent of the value of another parameter.

Use input parameters with sp\_iqobjectinfo; you can query the results of the sp\_iqobjectinfo and it performs better if you use input parameters rather than using predicates in the WHERE clause of the query. For example, Query A is written as:

```
SELECT COUNT(*) FROM sp_iqobjectinfo()
WHERE owner = 'HDLADMIN'
AND object_name = 'tab_case510'
AND object_type = 'table'
AND sub_object_name is NULL
AND dbspace_name = 'iqmain7'
AND partition_name = 'P1'
```

Query B is Query A rewritten to use sp\_iqobjectinfo input parameters:

```
SELECT COUNT(*) FROM sp_iqobjectinfo('HDLADMIN','tab_case510','table')
WHERE sub_object_name is NULL
AND dbspace_name = 'iqmain7'
AND PARTITION_NAME = 'P1'
```

Query B returns results faster than Query A. When the input parameters are passed to sp\_iqobjectinfo, the procedure compares and joins fewer records in the system tables, thus doing less work compared to Query A. In Query B, the predicates are applied in the procedure itself, which returns a smaller result set, so a smaller number of predicates is applied in the query.

The sp\_iqobjectinfo stored procedure supports wildcard characters for interpreting *<owner\_name\>*, *<object\_name\>*, and *<object\_type\>*. It shows information for all dbspaces that match the given pattern in the same way the LIKE clause matches patterns inside queries.



<a name="loioa5b0b72884f210158266fa85e5483c9c__iq_refbb_1680"/>

## Privileges

Requires EXECUTE object-level privilege on this procedure.



## Side Effects

None.



<a name="loioa5b0b72884f210158266fa85e5483c9c__iq_refbb_1685"/>

## Examples

This example returns information about all objects in the database:

```
CALL sp_iqobjectinfo;
```


<table>
<tr>
<th valign="top">

owner

</th>
<th valign="top">

object\_

name

</th>
<th valign="top">

sub\_object\_

name

</th>
<th valign="top">

object\_type

</th>
<th valign="top">

object\_id

</th>
<th valign="top">

id

</th>
<th valign="top">

dbspace\_name

</th>
<th valign="top">

partition\_name

</th>
</tr>
<tr>
<td valign="top">

HDLADMIN

</td>
<td valign="top">

T1

</td>
<td valign="top">

text\_index

</td>
<td valign="top">

index

</td>
<td valign="top">

12464

</td>
<td valign="top">

1750

</td>
<td valign="top">

user\_object\_store

</td>
<td valign="top">

NULL

</td>
</tr>
<tr>
<td valign="top">

MYSCHEMA1

</td>
<td valign="top">

R1

</td>
<td valign="top">

 

</td>
<td valign="top">

table

</td>
<td valign="top">

12473

</td>
<td valign="top">

1751

</td>
<td valign="top">

user\_object\_store

</td>
<td valign="top">

NULL

</td>
</tr>
<tr>
<td valign="top">

MYSCHEMA1

</td>
<td valign="top">

R1

</td>
<td valign="top">

a

</td>
<td valign="top">

column

</td>
<td valign="top">

12474

</td>
<td valign="top">

1751

</td>
<td valign="top">

user\_object\_store

</td>
<td valign="top">

NULL

</td>
</tr>
<tr>
<td valign="top">

USER1

</td>
<td valign="top">

r1

</td>
<td valign="top">

 

</td>
<td valign="top">

table

</td>
<td valign="top">

12479

</td>
<td valign="top">

1753

</td>
<td valign="top">

user\_object\_store

</td>
<td valign="top">

NULL

</td>
</tr>
<tr>
<td valign="top">

USER1

</td>
<td valign="top">

r1

</td>
<td valign="top">

a

</td>
<td valign="top">

column

</td>
<td valign="top">

12480

</td>
<td valign="top">

1753

</td>
<td valign="top">

user\_object\_store

</td>
<td valign="top">

NULL

</td>
</tr>
<tr>
<td valign="top">

USER1

</td>
<td valign="top">

r2

</td>
<td valign="top">

 

</td>
<td valign="top">

table

</td>
<td valign="top">

12489

</td>
<td valign="top">

1756

</td>
<td valign="top">

user\_object\_store

</td>
<td valign="top">

NULL

</td>
</tr>
<tr>
<td valign="top">

USER1

</td>
<td valign="top">

r2

</td>
<td valign="top">

a

</td>
<td valign="top">

column

</td>
<td valign="top">

12490

</td>
<td valign="top">

1756

</td>
<td valign="top">

user\_object\_store

</td>
<td valign="top">

NULL

</td>
</tr>
</table>

This example returns information about partitions and dbspace assignments of database object sale, owned by HDLADMIN, for table objects:

```
CALL sp_iqobjectinfo HDLADMIN,sale,'table';
```


<table>
<tr>
<th valign="top">

owner

</th>
<th valign="top">

object\_

name

</th>
<th valign="top">

sub\_object\_

name

</th>
<th valign="top">

object\_type

</th>
<th valign="top">

object\_id

</th>
<th valign="top">

id

</th>
<th valign="top">

dbspace\_name

</th>
<th valign="top">

partition\_name

</th>
</tr>
<tr>
<td valign="top">

HDLADMIN

</td>
<td valign="top">

sale

</td>
<td valign="top">

\(NULL\)

</td>
<td valign="top">

table

</td>
<td valign="top">

3698

</td>
<td valign="top">

742

</td>
<td valign="top">

iq\_main

</td>
<td valign="top">

\(NULL\)

</td>
</tr>
<tr>
<td valign="top">

HDLADMIN

</td>
<td valign="top">

sale

</td>
<td valign="top">

prod\_id

</td>
<td valign="top">

column

</td>
<td valign="top">

3699

</td>
<td valign="top">

742

</td>
<td valign="top">

iq\_main

</td>
<td valign="top">

\(NULL\)

</td>
</tr>
<tr>
<td valign="top">

HDLADMIN

</td>
<td valign="top">

sale

</td>
<td valign="top">

month\_num

</td>
<td valign="top">

column

</td>
<td valign="top">

3700

</td>
<td valign="top">

742

</td>
<td valign="top">

iq\_main

</td>
<td valign="top">

\(NULL\)

</td>
</tr>
<tr>
<td valign="top">

HDLADMIN

</td>
<td valign="top">

sale

</td>
<td valign="top">

rep\_id

</td>
<td valign="top">

column

</td>
<td valign="top">

3701

</td>
<td valign="top">

742

</td>
<td valign="top">

iq\_main

</td>
<td valign="top">

\(NULL\)

</td>
</tr>
<tr>
<td valign="top">

HDLADMIN

</td>
<td valign="top">

sale

</td>
<td valign="top">

sales

</td>
<td valign="top">

column

</td>
<td valign="top">

3702

</td>
<td valign="top">

742

</td>
<td valign="top">

iq\_main

</td>
<td valign="top">

\(NULL\)

</td>
</tr>
</table>

