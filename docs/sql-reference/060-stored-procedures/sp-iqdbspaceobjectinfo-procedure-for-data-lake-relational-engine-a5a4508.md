<!-- loioa5a4508c84f21015bbd8e6350bea7591 -->

# sp\_iqdbspaceobjectinfo Procedure for Data Lake Relational Engine

Lists objects and subobjects of type table \(including columns, indexes, metadata, primary keys, unique constraints, foreign keys, and partitions\) for a given dbspace.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



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

Requires EXECUTE object-level privilege on the procedure.



## Side Effects

None



<a name="loioa5a4508c84f21015bbd8e6350bea7591__iq_refbb_1525"/>

## Examples

These examples show objects in the iqdemo database to better illustrate output. iqdemo includes a sample user dbspace named iq\_main that may not be present in your own databases.

-   The following example displays information about a specific dbspace in the database:

    ```
    sp_iqdbspaceobjectinfo iq_main
    ```

    ```
    dbspace_name  dbspace_id object_type  owner   object_name  object_id  id  columns
    iq_main       16387      table        DBA     emp1           3689     741  4/4
    iq_main       16387      table        DBA     iq_dummy       3686     740  1/1
    iq_main       16387      table        DBA     sale           3698     742  4/4
    iq_main       16387      table        GROUPO  Contacts       3538     732  12/12
    iq_main       16387      table        GROUPO  Customers      3515     731  10/10
    iq_main       16387      table        GROUPO  Departments    3632     738  3/3
    iq_main       16387      table        GROUPO  Employees      3641     739  21/21
    iq_main       16387      table        GROUPO  FinancialCodes 3612     736  3/3
    iq_main       16387      table        GROUPO  FinancialData  3621     737  4/4
    iq_main       16387      table        GROUPO  Products       3593     735  8/8
    iq_main       16387      table        GROUPO  SalesOrderItems3580     734  5/5
    iq_main       16387      table        GROUPO  SalesOrders    3565     733  6/6
    
    indexes  metadata  primary_key  unique_constraint  foreign_key  partitions
    0/0      Y                   0  0/0                0/0          0/0
    0/0      Y                   0  0/0                0/0          0/0
    0/0      Y                   0  0/0                0/0          0/0
    0/0      Y                   1  0/0                1/1          0/0
    1/1      Y                   1  0/0                0/0          0/0
    0/0      Y                   1  0/0                1/1          0/0
    0/0      Y                   1  0/0                1/1          0/0
    0/0      Y                   1  0/0                0/0          0/0
    0/0      Y                   1  0/0                1/1          0/0
    4/4      Y                   1  0/0                0/0          0/0
    0/0      Y                   1  0/0                2/2          0/0
    0/0      Y                   1  0/0                3/3          0/0
    ```

-   The following example displays information about the objects owned by a specific user in a specific dbspace in the database:

    ```
    sp_iqdbspaceobjectinfo iq_main,GROUPO
    ```

    ```
    dbspace_name  dbspace_id object_type  owner   object_name    object_id  id  columns
    iq_main       16387      table        GROUPO  Contacts       3538       732 2/12
    iq_main       16387      table        GROUPO  Customers      3515       731 10/10
    iq_main       16387      table        GROUPO  Departments    3632       738 3/3
    iq_main       16387      table        GROUPO  Employees      3641       739 21/21
    iq_main       16387      table        GROUPO  FinancialCodes 3612       736 3/3
    iq_main       16387      table        GROUPO  FinancialData  3621       737 4/4
    iq_main       16387      table        GROUPO  Products       3593       735 8/8
    iq_main       16387      table        GROUPO  SalesOrderItems3580       734 5/5
    iq_main       16387      table        GROUPO  SalesOrders    3565       733 6/6
    
    indexes  metadata  primary_key  unique_constraint  foreign_key  partitions
    0/0      Y                   1  0/0                1/1          0/0
    1/1      Y                   1  0/0                0/0          0/0
    0/0      Y                   1  0/0                1/1          0/0
    0/0      Y                   1  0/0                1/1          0/0
    0/0      Y                   1  0/0                0/0          0/0
    0/0      Y                   1  0/0                1/1          0/0
    4/4      Y                   1  0/0                0/0          0/0
    0/0      Y                   1  0/0                2/2          0/0
    0/0      Y                   1  0/0                3/3          0/0
    ```

-   In this example, the commands move all tables on dbspace\_x to dbspace\_y:

    ```
    SELECT 'ALTER TABLE ' || owner || '.' || 
    object_name || ' MOVE TO dbspace_y;'
    FROM sp_iqdbspaceobjectinfo()
    WHERE object_type = 'table' AND
    dbspace_name = 'dbspace_x';
    ```

    The result are the following ALTER TABLE commands:

    ```
    ALTER TABLE DBA.dt1 MOVE TO dbspace_y;
    ALTER TABLE DBA.dt2 MOVE TO dbspace_y;
    ALTER TABLE DBA.dt3 MOVE TO dbspace_y;
    ```


