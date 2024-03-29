<!-- loioa5a872a584f21015ba4c951765fe55ca -->

# sp\_iqevent Procedure for Data Lake Relational Engine

Displays information about system and user-defined events.



<a name="loioa5a872a584f21015ba4c951765fe55ca__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqevent [ <event-name> ], [ <event-owner> ], [ <event-type> ]
```



<a name="loioa5a872a584f21015ba4c951765fe55ca__iq_refbb_1564"/>

## Parameters


<dl>
<dt><b>

*<event-name\>*

</b></dt>
<dd>

The name of the event.



</dd><dt><b>

*<event-owner\>*

</b></dt>
<dd>

The owner of the event.



</dd><dt><b>

*<event-type\>*

</b></dt>
<dd>

The type of event. Allowed values are:

-   SYSTEM – displays information about system events \(events owned by user SYS or dbo\) only
-   ALL – displays information about user and system events
-   Any other value – displays information about user events



</dd>
</dl>



<a name="loioa5a872a584f21015ba4c951765fe55ca__section_ztj_rlz_mbb"/>

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

event\_name

</td>
<td valign="top">

The name of the event.

</td>
</tr>
<tr>
<td valign="top">

event\_owner

</td>
<td valign="top">

The owner of the event.

</td>
</tr>
<tr>
<td valign="top">

event\_type

</td>
<td valign="top">

For system events, the event type as listed in the SYSEVENTTYPE system table.

</td>
</tr>
<tr>
<td valign="top">

enabled

</td>
<td valign="top">

Indicates whether or not the event is allowed to fire \(Y/N\).

</td>
</tr>
<tr>
<td valign="top">

action

</td>
<td valign="top">

The event handler definition.

</td>
</tr>
<tr>
<td valign="top">

condition

</td>
<td valign="top">

The WHERE condition used to control firing of the event handler.

</td>
</tr>
<tr>
<td valign="top">

location

</td>
<td valign="top">

The location where the event is allowed to fire:

-   C – consolidated
-   R – remote
-   A – all



</td>
</tr>
<tr>
<td valign="top">

remarks

</td>
<td valign="top">

A comment string.

</td>
</tr>
</table>



<a name="loioa5a872a584f21015ba4c951765fe55ca__section_pr3_qlz_mbb"/>

## Remarks

The sp\_iqevent procedure can be invoked without any parameters. If no parameters are specified, only information about user events \(events not owned by dbo or SYS\) is displayed by default.

If you do not specify either of the first two parameters, but specify the next parameter in the sequence, you need to substitute NULL for the omitted parameters. For example: `sp_iqevent NULL, NULL, SYSTEM` and sp\_iqevent NULL, user1.

The sp\_iqevent stored event displays information about events in a database. If you specify one or more parameters, the result is filtered by the specified parameters. For example, if *<event-name\>* is specified, only information about the specified event is displayed. If *<event-owner\>* is specified, sp\_iqevent only returns information about events owned by the specified owner. If no parameters are specified, sp\_iqevent displays information about all the user events in the database.



<a name="loioa5a872a584f21015ba4c951765fe55ca__iq_refbb_1563"/>

## Privileges

Requires EXECUTE object-level privilege on the procedure.



## Side Effects

None



<a name="loioa5a872a584f21015ba4c951765fe55ca__iq_refbb_1569"/>

## Examples

-   This example displays information about all user events in the database:

    ```
    CALL sp_iqevent;
    ```

-   This example displays information about the user-defined event e1:

    ```
    CALL sp_iqevent e1;
    ```


    <table>
    <tr>
    <th valign="top">

    event\_name
    
    </th>
    <th valign="top">

    event\_owner
    
    </th>
    <th valign="top">

    event\_type
    
    </th>
    <th valign="top">

    enabled
    
    </th>
    <th valign="top">

    action
    
    </th>
    <th valign="top">

    condition
    
    </th>
    <th valign="top">

    location
    
    </th>
    <th valign="top">

    remarks
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    e1
    
    </td>
    <td valign="top">
    
    DBA
    
    </td>
    <td valign="top">
    
    \(NULL\)
    
    </td>
    <td valign="top">
    
    Y
    
    </td>
    <td valign="top">
    
    \(NULL\)
    
    </td>
    <td valign="top">
    
    \(NULL\)
    
    </td>
    <td valign="top">
    
    A
    
    </td>
    <td valign="top">
    
    \(NULL\)
    
    </td>
    </tr>
    </table>
    
-   This example displays information about all system events:

    ```
    CALL sp_iqevent NULL, NULL, SYSTEM;
    ```


    <table>
    <tr>
    <th valign="top">

    event\_name
    
    </th>
    <th valign="top">

    event\_owner
    
    </th>
    <th valign="top">

    event\_type
    
    </th>
    <th valign="top">

    enabled
    
    </th>
    <th valign="top">

    action
    
    </th>
    <th valign="top">

    condition
    
    </th>
    <th valign="top">

    location
    
    </th>
    <th valign="top">

    remarks
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    ev\_iqbegintxn
    
    </td>
    <td valign="top">
    
    dbo
    
    </td>
    <td valign="top">
    
    IQTLVAvailable
    
    </td>
    <td valign="top">
    
    Y
    
    </td>
    <td valign="top">
    
    begin call dbo.sp\_iqlog...
    
    </td>
    <td valign="top">
    
    \(NULL\)
    
    </td>
    <td valign="top">
    
    A
    
    </td>
    <td valign="top">
    
    \(NULL\)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    ev\_iqmpxcompact
    
    </td>
    <td valign="top">
    
    dbo
    
    </td>
    <td valign="top">
    
    \(NULL\)
    
    </td>
    <td valign="top">
    
    N
    
    </td>
    <td valign="top">
    
    begin Declare\_Catalog...
    
    </td>
    <td valign="top">
    
    \(NULL\)
    
    </td>
    <td valign="top">
    
    A
    
    </td>
    <td valign="top">
    
    \(NULL\)
    
    </td>
    </tr>
    </table>
    
-   In this example, no rows returned, as the event non\_existing\_event does not exist:

    ```
    CALL sp_iqevent non_existing_event;
    ```

-   This example displays information about all events owned by DBA:

    ```
    CALL sp_iqevent NULL, DBA;
    ```

-   This example displays information about the event e1 owned by DBA:

    ```
    CALL sp_iqevent e1, DBA;
    ```

-   In this example, ev\_iqbegintxn is a system-defined event. If there is no user-defined event also named ev\_iqbegintxn, no rows are returned. \(By default, only user-defined events are returned\):

    ```
    CALL sp_iqevent ev_iqbegintxn;
    ```

-   In this example, no rows are returned, as the event ev\_iqbegintxn is not a user event \(by default only user events returned\):

    ```
    CALL sp_iqevent ev_iqbegintxn, dbo;
    ```

-   This example displays information about all system events \(owned by dbo or SYS\):

    ```
    CALL sp_iqevent NULL, NULL, SYSTEM;
    ```

-   This example displays information about the system event ev\_iqbegintxn:

    ```
    CALL sp_iqevent ev_iqbegintxn, NULL, SYSTEM;
    ```

-   This example displays information about the system event ev\_iqbegintxn owned by dbo:

    ```
    CALL sp_iqevent ev_iqbegintxn, dbo, ALL;
    ```


**Related Information**  


[sp\_iqcolumn Procedure for Data Lake Relational Engine](sp-iqcolumn-procedure-for-data-lake-relational-engine-a59eafa.md "Displays information about columns in a database.")

[sp\_iqconstraint Procedure for Data Lake Relational Engine](sp-iqconstraint-procedure-for-data-lake-relational-engine-a5a0395.md "Lists referential integrity constraints defined using CREATE TABLE or ALTER TABLE for the specified table or column.")

[sp\_iqdatatype Procedure for Data Lake Relational Engine](sp-iqdatatype-procedure-for-data-lake-relational-engine-a5a247c.md "Displays information about system data types and user-defined data types.")

[sp\_iqhelp Procedure for Data Lake Relational Engine](sp-iqhelp-procedure-for-data-lake-relational-engine-a5a978b.md "Displays information about system and user-defined objects and data types.")

[sp\_iqindex and sp\_iqindex\_alt Procedures for Data Lake Relational Engine](sp-iqindex-and-sp-iqindex-alt-procedures-for-data-lake-relational-engine-a5aa7ea.md "Lists information about indexes.")

[sp\_iqpkeys Procedure for Data Lake Relational Engine](sp-iqpkeys-procedure-for-data-lake-relational-engine-a5b1c11.md "Displays information about primary keys and primary key constraints by table, column, table owner, or for all data lake Relational Engine tables in the database.")

[sp\_iqprocparm Procedure for Data Lake Relational Engine](sp-iqprocparm-procedure-for-data-lake-relational-engine-a5b2c2d.md "Displays information about stored procedure parameters, including result set variables and SQLSTATE/SQLCODE error values.")

[sp\_iq\_reset\_identity Procedure for Data Lake Relational Engine](sp-iq-reset-identity-procedure-for-data-lake-relational-engine-a5b4402.md "Sets the seed of the Identity/Autoincrement column associated with the specified table to the specified value.")

[sp\_iqtable Procedure for Data Lake Relational Engine](sp-iqtable-procedure-for-data-lake-relational-engine-a5b959d.md "Displays information about tables in the database.")

[sp\_iqview Procedure for Data Lake Relational Engine](sp-iqview-procedure-for-data-lake-relational-engine-a5bdee7.md "Displays information about views in a database.")

