<!-- loioa5a3ca6f84f21015b8efef1f7e569fe6 -->

# sp\_iqdbspaceinfo Procedure for Data Lake Relational Engine

Displays the size of each object and subobject used in the specified table.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqdbspaceinfo [ <dbspace-name> ]
 [, <owner_name> ] [, <object_name> ] [, <object-type> ]
```



<a name="loioa5a3ca6f84f21015b8efef1f7e569fe6__iq_refbb_1513"/>

## Parameters

 *<dbspace-name\>*
 :   \(Optional\) If specified, sp\_iqdbspaceinfo displays one line for each table that has any component in the specified dbspace. Otherwise, the procedure shows information for all dbspaces in the database.

  *<owner\_name\>*
 :   \(Optional\) Owner of the object. If specified, sp\_iqdbspaceinfo displays output only for tables with the specified owner. If not specified, sp\_iqdbspaceinfo displays information on tables for all users in the database.

  *<object\_name\>*
 :   \(Optional\) Name of the table. If not specified, sp\_iqdbspaceinfo displays information on all tables in the database.

  *<object\_type\>*
 :   \(Optional\) Valid table objects.

 

<a name="loioa5a3ca6f84f21015b8efef1f7e569fe6__section_d5y_dqz_mbb"/>

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

To run this procedure, you need the EXECUTE privilege on the procedure. See [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md). 



## Side Effects

None



<a name="loioa5a3ca6f84f21015b8efef1f7e569fe6__iq_refbb_1518"/>

## Examples

These examples show objects in the iqdemo database to better illustrate output. iqdemo includes a sample user dbspace named iq\_main that may not be present in your own databases.

-   The following example displays the size of all objects and subobjects in all tables in all dbspaces in the database:

    ```
    sp_iqdbspaceinfo
    ```

    ```
    dbspace_name    object_type  owner   object_name     object_id  id   columns
    iq_main         table        DBA     emp1              3689     741   96K
    iq_main         table        DBA     iq_dummy          3686     740   24K
    iq_main         table        DBA     sale              3698     742   96K
    iq_main         table        GROUPO  Contacts          3538     732   288K
    iq_main         table        GROUPO  Customers         3515     731   240K
    iq_main         table        GROUPO  Departments       3632     738   72K
    iq_main         table        GROUPO  Employees         3641     739   408K
    iq_main         table        GROUPO  FinancialCodes    3612     736   72K
    iq_main         table        GROUPO  FinancialData     3621     737   96K
    iq_main         table        GROUPO  Products          3593     735   272K
    iq_main         table        GROUPO  SalesOrderItems   3580     734   120K
    iq_main         table        GROUPO  SalesOrders       3565     733   144K
    
    indexes  metadata  primary_key  unique_constraint  foreign_key  dbspace_online  is_dbspace_preallocate
    0B       1.37M     0B           0B                 0B           Y               T 
    0B       464K      0B           0B                 0B           Y               T              
    0B       1.22M     0B           0B                 0B           Y               T
    0B       5.45M     24K          0B                 48K          Y               T
    48K      4.63M     24K          0B                 0B           Y               T
    0B       1.78M     24K          0B                 48K          Y               T
    0B       8.03M     24K          0B                 48K          Y               T
    0B       1.53M     24K          0B                 0B           Y               T
    0B       2.19M     24K          0B                 48K          Y               T
    192K     4.67M     24K          0B                 0B           Y               T
    0B       2.7M      24K          0B                 104K         Y               T
    0B       3.35M     24K          0B                 144K         Y               T
    ```

-   The following example displays the size of all objects and subobjects owned by a specified user in a specified dbspace in the database:

    ```
    sp_iqdbspaceinfo iq_main,GROUPO
    ```

    ```
    dbspace_name    object_type  owner   object_name     object_id  id   columns
    iq_main         table        GROUPO  Contacts          3538     732   288K
    iq_main         table        GROUPO  Customers         3515     731   240K
    iq_main         table        GROUPO  Departments       3632     738   72K
    iq_main         table        GROUPO  Employees         3641     739   408K
    iq_main         table        GROUPO  FinancialCodes    3612     736   72K
    iq_main         table        GROUPO  FinancialData     3621     737   96K
    iq_main         table        GROUPO  Products          3593     735   272K
    iq_main         table        GROUPO  SalesOrderItems   3580     734   120K
    iq_main         table        GROUPO  SalesOrders       3565     733   144K
    
    indexes  metadata  primary_key  unique_constraint  foreign_key  dbspace_online  is_dbspace_preallocate
    0B       5.45M     24K          0B                 48K          Y               T
    48K      4.63M     24K          0B                 0B           Y               T
    0B       1.78M     24K          0B                 48K          Y               T
    0B       8.03M     24K          0B                 48K          Y               T
    0B       1.53M     24K          0B                 0B           Y               T
    0B       2.19M     24K          0B                 48K          Y               T
    192K     4.67M     24K          0B                 0B           Y               T
    0B       2.7M      24K          0B                 104K         Y               T
    0B       3.35M     24K          0B                 144K         Y               T
    ```

-   The following example displays the size of a specified object and its subobjects owned by a specified user in a specified dbspace in the database:

    ```
    sp_iqdbspaceinfo iq_main,GROUPO,Departments
    ```


**Related Information**  


[sp\_iqindexinfo Procedure for Data Lake Relational Engine](sp-iqindexinfo-procedure-for-data-lake-relational-engine-a5ac909.md "Displays the number of blocks (objects) used per index per main dbspace for a given object. If the object resides on several dbspaces, sp_iqindexinfo returns the space used in all dbspaces, as shown in the example.")

[sp\_iqdbspace Procedure for Data Lake Relational Engine](sp-iqdbspace-procedure-for-data-lake-relational-engine-a5a34b5.md "Displays detailed information about each data lake Relational Engine dbspace.")

[sp\_iqspaceinfo Procedure for Data Lake Relational Engine](sp-iqspaceinfo-procedure-for-data-lake-relational-engine-a5b6d30.md "Displays the number of blocks (objects) used by each object in the current database and the name of the dbspace in which the object is located.")

