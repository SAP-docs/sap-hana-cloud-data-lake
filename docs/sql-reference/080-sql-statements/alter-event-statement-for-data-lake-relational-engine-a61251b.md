<!-- loioa61251b484f21015bebaad7232f40857 -->

# ALTER EVENT Statement for Data Lake Relational Engine

Changes the definition of an event or its associated handler for automating predefined actions. Also alters the definition of scheduled actions.



<a name="loioa61251b484f21015bebaad7232f40857__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
ALTER EVENT <event-name>
   [ DELETE TYPE | TYPE <event-type> ]
   { WHERE { <trigger-condition> | NULL }
    | { ADD | [ MODIFY ] | DELETE } SCHEDULE <schedule-spec> }
   [ ENABLE | DISABLE ]
   [ [ MODIFY ] HANDLER <compound-statement> | DELETE HANDLER }
```

```
<event-type> ::=
   { BackupEnd 
   |  "Connect"  
   |  ConnectFailed 
   |  DatabaseStart 
   |  DBDiskSpace 
   |  "Disconnect" 
   |  GlobalAutoincrement 
   |  GrowDB 
   |  GrowLog 
   |  GrowTemp   
   |  IQMainDBSpaceFree 
   |  IQTempDBSpaceFree 
   |  LogDiskSpace 
   |  "RAISERROR" 
   |  ServerIdle 
   |  TempDiskSpace }
```

```
<trigger-condition> ::=
   event_condition( <condition-name> ) 
   { = 
   | < 
   | > 
   | != 
   | <= 
   | >= } <value>
```

```
<schedule-spec> ::=
   [ <schedule-name> ] 
   { START TIME <start-time> 
      | BETWEEN <start-time> AND <end-time> } 
   [ EVERY <period> { HOURS | MINUTES | SECONDS } ] 
   [ ON { ( <day-of-week>, … ) 
      | ( <day-of-month>, … ) } ] 
   [ START DATE <start-date> ]
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa61251b484f21015bebaad7232f40857__alter_event_parm1"/>

## Parameters


<dl>
<dt><b>

DELETE TYPE

</b></dt>
<dd>

Removes an association of the event with an event type.



</dd><dt><b>

ADD | MODIFY | DELETE SCHEDULE

</b></dt>
<dd>

 Changes the definition of a schedule. Only one schedule can be altered in any one ALTER EVENT statement.



</dd><dt><b>

WHERE *<trigger-condition\>*

</b></dt>
<dd>

The trigger condition determines the condition under which an event is fired. For example, to take an action when the storage space containing the transaction log becomes more than 80 percent full, use this triggering condition:

```
...
              WHERE event_condition( 'LogDiskSpacePercentFree' ) < 20
              ...
```

The argument to the EVENT\_CONDITION function must be valid for the event type. You can use multiple AND conditions to make up the WHERE clause, but you cannot use OR conditions or other conditions.

You can specify a variable name for the event\_condition value.



</dd><dt><b>

TYPE *<event-type\>*

</b></dt>
<dd>

One of a set of system-defined event types. The event types are case-insensitive. To specify the conditions under which this *<event-type\>* triggers the event, use the WHERE clause.


<dl>
<dt><b>

BackupEnd

</b></dt>
<dd>

Take action at the end of a backup.



</dd><dt><b>

Connect / ConnectFailed

</b></dt>
<dd>

When a connection is made \(Connect\) or when a connection attempt fails \(ConnectFailed\), you may want to use these events for security purposes. As an alternative to a connect event handler, you may want to consider using a login procedure.



</dd><dt><b>

DatabaseStart

</b></dt>
<dd>

Take action when a database is started.



</dd><dt><b>

Disconnect

</b></dt>
<dd>

Take action when a user or application disconnects.



</dd><dt><b>

Diskspace

</b></dt>
<dd>

Tracks the available space on the device holding the database file \(DBDiskSpace\), the transaction log file \(LogDiskSpace\), or temporary file \(TempDiskSpace\).

If the database contains an event handler for one of the DiskSpace types, the database server checks the available space on each device associated with the relevant file every 30 seconds.

In the event the database has more than one dbspace, on separate drives, DBDiskSpace checks each drive and acts depending on the lowest available space.

LogDiskSpace checks the location of the transaction log and any mirrored transaction log, and reports based on the least available space.



</dd><dt><b>

File size

</b></dt>
<dd>

Take action when the file reaches a specified size. This can be used for the database file \(GrowDB\), the transaction log \(GrowLog\), or the temporary file \(GrowTemp\).

You may want to use file size events to track unusual actions on the database, or monitor bulk operations.



</dd><dt><b>

GlobalAutoincrement

</b></dt>
<dd>

When the number of remaining values for a column defined with GLOBAL AUTOINCREMENT is within one percent of its range, the GlobalAutoincrement event fires. A typical action for the handler could be to request a new value for the GLOBAL\_DATABASE\_ID clause.

You can use the `EVENT_CONDITION` function with RemainingValues as an argument for this event type. RemainingValues returns the number of remaining values that can be generated for the column, while TableName returns the table containing the GLOBAL AUTOINCREMENT column that is near the end of its range.



</dd><dt><b>

RAISERROR

</b></dt>
<dd>

When a RAISERROR statement is executed, you can use the RAISERROR event type to take actions. The error number used in the RAISERROR statement can be determined within the event handler using the EVENT\_CONDITION function \(for example, `EVENT_CONDITION( 'ErrorNumber' )`\).



</dd><dt><b>

ServerIdle

</b></dt>
<dd>

If the database contains an event handler for the ServerIdle type, the server checks for server activity every 30 seconds.



</dd>
</dl>



</dd>
</dl>



<a name="loioa61251b484f21015bebaad7232f40857__alter_event_remarks1"/>

## Remarks

ALTER EVENT lets you alter an event definition created with CREATE EVENT. Possible uses include:

-   Change an event handler during development.
-   Define and test an event handler without a trigger condition or schedule during a development phase, and then add the conditions for execution using ALTER EVENT once the event handler is completed.
-   Disable an event handler temporarily by disabling the event.

When you alter an event using ALTER EVENT, specify the event name and, optionally, the schedule name.

Each event has a unique event ID. Use the event\_id columns of `SYSEVENT` and `SYSSCHEDULE` to match the event to the associated schedule.

> ### Note:  
> For **required** parameters that accept variable names, an error is returned if one of the following conditions is true:
> 
> -   The variable doesn't exist
> -   The contents of the variable are NULL
> -   The variable exceeds the length allowed by the parameter
> -   The data type of the variable doesn't match that required by the parameter



<a name="loioa61251b484f21015bebaad7232f40857__IQ_Permissions"/>

## Privileges

Requires one of:

-   MANAGE EVENT system privilege to alter self-owned events.
-   MANAGE ANY EVENT system privilege to alter any event owned by any user.
-   ALTER ANY OBJECT system privilege to alter any event owned by any user.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



<a name="loioa61251b484f21015bebaad7232f40857__alter_event_sideefects1"/>

## Side Effects

Automatic commit



<a name="loioa61251b484f21015bebaad7232f40857__alter_event_eamples1"/>

## Examples

-   The following example lists event names by querying the system table `SYSEVENT`:

    ```
    SELECT event_id, event_name FROM SYS.SYSEVENT;
    ```

-   The following example lists schedule names by querying the system table `SYSSCHEDULE`:

    ```
    SELECT event_id, sched_name FROM SYS.SYSSCHEDULE;
    ```


**Related Information**  


[CREATE EVENT Statement for Data Lake Relational Engine](create-event-statement-for-data-lake-relational-engine-a617091.md "Defines an event and its associated handler for automating predefined actions. Also defines scheduled actions.")

[BEGIN … END Statement for Data Lake Relational Engine](begin-end-statement-for-data-lake-relational-engine-a6142de.md "Groups SQL statements together.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[DROP EVENT Statement for Data Lake Relational Engine](drop-event-statement-for-data-lake-relational-engine-6dca296.md "Removes an event from the database.")

