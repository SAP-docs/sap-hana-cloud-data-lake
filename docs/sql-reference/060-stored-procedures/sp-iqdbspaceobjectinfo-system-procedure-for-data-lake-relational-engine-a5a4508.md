<!-- loioa5a4508c84f21015bbd8e6350bea7591 -->

# sp\_iqdbspaceobjectinfo System Procedure for Data Lake Relational Engine

Lists objects and subobjects of type table \(including columns, indexes, metadata, primary keys, unique constraints, foreign keys, and partitions\) for a given dbspace.



<a name="loioa5a4508c84f21015bbd8e6350bea7591__section_j5b_wvh_b4b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqdbspaceobjectinfo [ <dbspace-name> ]
 [ , <owner_name> ] [ ,  <object_name> ] [ , <object-type> ]
```



<a name="loioa5a4508c84f21015bbd8e6350bea7591__iq_refbb_1521"/>

## Parameters


<dl>
<dt><b>

*<dbspace-name\>*

</b></dt>
<dd>

\(Optional\) If specified, sp\_iqdbspaceobjectinfo displays output only for the specified dbspace. Otherwise, it shows information for all dbspaces in the database.



</dd><dt><b>

*<owner\_name\>*

</b></dt>
<dd>

\(Optional\) Owner of the object. If specified, sp\_iqdbspaceobjectinfo displays output only for tables with the specified owner. If not specified, sp\_iqdbspaceobjectinfo displays information for tables for all users in the database.



</dd><dt><b>

*<object\_name\>*

</b></dt>
<dd>

\(Optional\) Name of the table. If not specified, sp\_iqdbspaceobjectinfo displays information for all tables in the database.



</dd><dt><b>

*<object-type\>*

</b></dt>
<dd>

\(Optional\) Valid object types for table objects.



</dd>
</dl>



<a name="loioa5a4508c84f21015bbd8e6350bea7591__section_un4_ppz_mbb"/>

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

Name of the dbspace.

</td>
</tr>
<tr>
<td valign="top">

dbspace\_id

</td>
<td valign="top">

Identifier of the dbspace.

</td>
</tr>
<tr>
<td valign="top">

object\_type

</td>
<td valign="top">

Table.

</td>
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

Name of the table object on the dbspace.

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

columns

</td>
<td valign="top">

Number of table columns located on the given dbspace. If a column or one of the column-partitions is located on a dbspace, it is counted to be present on that dbspace. The result is shown in the form n/N \(n out of total N columns of the table are on the given dbspace\).

</td>
</tr>
<tr>
<td valign="top">

indexes

</td>
<td valign="top">

Number of user-defined indexes on the table located on the given dbspace. Shown in the form n/N \(n out of total N indexes on the table are on the given dbspace\). This does not contain indexes, which are system-generated, such as FP indexes and HG indexes in the case of unique constraints.

</td>
</tr>
<tr>
<td valign="top">

metadata

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

primary\_key

</td>
<td valign="top">

Boolean field \(1/0\) that denotes whether the primary key of the table, if any, is located on this dbspace.Boolean field \(Y/N\) that denotes whether the metadata information of the subobject is also located on this dbspace.

</td>
</tr>
<tr>
<td valign="top">

unique\_constraint

</td>
<td valign="top">

Number of unique constraints on the table that are located on the given dbspace. Appears in the form n/N \(n out of total N unique constraints on the table are in the given dbspace\).

</td>
</tr>
<tr>
<td valign="top">

foreign\_key

</td>
<td valign="top">

Boolean fieldNumber of foreign\_keys on the table that are located on the given dbspace. Appears in the form n/N \(n out of total N foreign keys on the table are in the given dbspace\).

</td>
</tr>
<tr>
<td valign="top">

partitions

</td>
<td valign="top">

Number of partitions of the table that are located on the given dbspace. Appears in the form n/N \(n out of total N partitions of the table are in the given dbspace\).

</td>
</tr>
</table>



<a name="loioa5a4508c84f21015bbd8e6350bea7591__iq_refbb_1523"/>

## Remarks

All parameters are optional and any parameter may be supplied independent of the value of other parameters.

The sp\_iqdbspaceobjectinfo stored procedure supports wildcard characters for interpreting *<dbspace\_name\>*, *<object\_name\>*, and *<owner\_name\>*. It displays information for all dbspaces that match the given pattern in the same way as the LIKE clause matches patterns inside queries.

For tables, sp\_iqdbspaceobjectinfo displays summary information for all associated subobjects sorted by dbspace\_name, owner and object\_name.



<a name="loioa5a4508c84f21015bbd8e6350bea7591__iq_refbb_1520"/>

## Privileges

Requires EXECUTE object-level privilege on this procedure.



## Side Effects

None.



<a name="loioa5a4508c84f21015bbd8e6350bea7591__iq_refbb_1525"/>

## Examples

This example returns information about dbspace user\_object\_store:

```
sp_iqdbspaceobjectinfo;
```


<table>
<tr>
<th valign="top">

dbspace\_name

</th>
<th valign="top">

dbspace\_

id

</th>
<th valign="top">

object\_

type

</th>
<th valign="top">

owner

</th>
<th valign="top">

object\_

name

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

indexes

</th>
<th valign="top">

metadata

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

partitions

</th>
</tr>
<tr>
<td valign="top">

user\_object\_store

</td>
<td valign="top">

16388

</td>
<td valign="top">

table

</td>
<td valign="top">

HDLADMIN

</td>
<td valign="top">

Sales

</td>
<td valign="top">

14386

</td>
<td valign="top">

1764

</td>
<td valign="top">

01-Jan

</td>
<td valign="top">

0/0

</td>
<td valign="top">

Y

</td>
<td valign="top">

0

</td>
<td valign="top">

0/0

</td>
<td valign="top">

0/0

</td>
<td valign="top">

0/0

</td>
</tr>
<tr>
<td valign="top">

user\_object\_store

</td>
<td valign="top">

16388

</td>
<td valign="top">

table

</td>
<td valign="top">

USER1

</td>
<td valign="top">

Customer

</td>
<td valign="top">

14394

</td>
<td valign="top">

1767

</td>
<td valign="top">

03-Mar

</td>
<td valign="top">

0/0

</td>
<td valign="top">

Y

</td>
<td valign="top">

0

</td>
<td valign="top">

0/0

</td>
<td valign="top">

0/0

</td>
<td valign="top">

0/0

</td>
</tr>
<tr>
<td valign="top">

user\_object\_store

</td>
<td valign="top">

16388

</td>
<td valign="top">

table

</td>
<td valign="top">

USER1

</td>
<td valign="top">

OrderItem

</td>
<td valign="top">

12479

</td>
<td valign="top">

1753

</td>
<td valign="top">

01-Jan

</td>
<td valign="top">

0/0

</td>
<td valign="top">

Y

</td>
<td valign="top">

0

</td>
<td valign="top">

0/0

</td>
<td valign="top">

0/0

</td>
<td valign="top">

0/0

</td>
</tr>
<tr>
<td valign="top">

user\_object\_store

</td>
<td valign="top">

16388

</td>
<td valign="top">

table

</td>
<td valign="top">

USER1

</td>
<td valign="top">

SalesOrder

</td>
<td valign="top">

12489

</td>
<td valign="top">

1756

</td>
<td valign="top">

01-Jan

</td>
<td valign="top">

0/0

</td>
<td valign="top">

Y

</td>
<td valign="top">

0

</td>
<td valign="top">

0/0

</td>
<td valign="top">

0/0

</td>
<td valign="top">

0/0

</td>
</tr>
<tr>
<td valign="top">

user\_object\_store

</td>
<td valign="top">

16388

</td>
<td valign="top">

mat view

</td>
<td valign="top">

USER1

</td>
<td valign="top">

Products

</td>
<td valign="top">

14401

</td>
<td valign="top">

1768

</td>
<td valign="top">

02-Feb

</td>
<td valign="top">

0/0

</td>
<td valign="top">

Y

</td>
<td valign="top">

0

</td>
<td valign="top">

0/0

</td>
<td valign="top">

0/0

</td>
<td valign="top">

0/0

</td>
</tr>
</table>

This example displays information about all objects in the dbspace owned by USER1

```
sp_iqdbspaceobjectinfo (NULL, 'USER1');
```

