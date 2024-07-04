<!-- loioa5a872a584f21015ba4c951765fe55ca -->

# sp\_iqevent System Procedure for Data Lake Relational Engine

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

Requires EXECUTE object-level privilege on this procedure.



## Side Effects

None



<a name="loioa5a872a584f21015ba4c951765fe55ca__iq_refbb_1569"/>

## Examples

This example returns information about the user-defined event event1:

```
CALL sp_iqevent event1;
```


<table>
<tr>
<th valign="top">

event\_

name

</th>
<th valign="top">

event\_

owner

</th>
<th valign="top">

event\_

type

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

event1

</td>
<td valign="top">

USER1

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

This example returns information about all user events in the database:

```
CALL sp_iqevent;
```

This example returns information about all system events:

```
CALL sp_iqevent NULL, NULL, SYSTEM;
```


<table>
<tr>
<th valign="top">

event\_

name

</th>
<th valign="top">

event\_

owner

</th>
<th valign="top">

event\_

type

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

ev\_iqbegintxn is a system-defined event. If there is no user-defined event also named ev\_iqbegintxn, no rows are returned. \(By default, only user-defined events are returned\):

```
CALL sp_iqevent ev_iqbegintxn;
```

This example returns information about all system events \(owned by dbo or SYS\):

```
CALL sp_iqevent NULL, NULL, SYSTEM;
```

This example returns information about the system event ev\_iqbegintxn:

```
CALL sp_iqevent ev_iqbegintxn, NULL, SYSTEM;
```

**Related Information**  


[sp\_iqcolumn System Procedure for Data Lake Relational Engine](sp-iqcolumn-system-procedure-for-data-lake-relational-engine-a59eafa.md "Displays information about columns in a database.")

[sp\_iqconstraint System Procedure for Data Lake Relational Engine](sp-iqconstraint-system-procedure-for-data-lake-relational-engine-a5a0395.md "Lists referential integrity constraints defined using CREATE TABLE or ALTER TABLE for the specified table or column.")

[sp\_iqdatatype System Procedure for Data Lake Relational Engine](sp-iqdatatype-system-procedure-for-data-lake-relational-engine-a5a247c.md "Displays information about system data types and user-defined data types.")

[sp\_iqhelp System Procedure for Data Lake Relational Engine](sp-iqhelp-system-procedure-for-data-lake-relational-engine-a5a978b.md "Displays information about system and user-defined objects and data types.")

[sp\_iqindex and sp\_iqindex\_alt System Procedures for Data Lake Relational Engine](sp-iqindex-and-sp-iqindex-alt-system-procedures-for-data-lake-relational-engine-a5aa7ea.md "Lists information about indexes.")

[sp\_iqpkeys System Procedure for Data Lake Relational Engine](sp-iqpkeys-system-procedure-for-data-lake-relational-engine-a5b1c11.md "Displays information about primary keys and primary key constraints by table, column, table owner, or for all data lake Relational Engine tables in the database.")

[sp\_iqprocparm System Procedure for Data Lake Relational Engine](sp-iqprocparm-system-procedure-for-data-lake-relational-engine-a5b2c2d.md "Displays information about stored procedure parameters, including result set variables and SQLSTATE/SQLCODE error values.")

[sp\_iq\_reset\_identity System Procedure for Data Lake Relational Engine](sp-iq-reset-identity-system-procedure-for-data-lake-relational-engine-a5b4402.md "Sets the seed of the Identity/Autoincrement column associated with the specified table to the specified value.")

[sp\_iqtable System Procedure for Data Lake Relational Engine](sp-iqtable-system-procedure-for-data-lake-relational-engine-a5b959d.md "Displays information about tables in the database.")

[sp\_iqview System Procedure for Data Lake Relational Engine](sp-iqview-system-procedure-for-data-lake-relational-engine-a5bdee7.md "Displays information about views in a database.")

