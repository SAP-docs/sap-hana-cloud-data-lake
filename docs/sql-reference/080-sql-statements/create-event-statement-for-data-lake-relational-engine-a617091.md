<!-- loioa617091784f210158db2e43f0733ae5d -->

# CREATE EVENT Statement for Data Lake Relational Engine

Defines an event and its associated handler for automating predefined actions. Also defines scheduled actions.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
CREATE [ OR REPLACE ] EVENT <event-name>
   [ { TYPE <event-type> [ WHERE <trigger-condition> [ AND <trigger-condition> ], ...]
     | SCHEDULE <schedule-spec>, …  } ]
   [ ENABLE | DISABLE ]
   [ HANDLER
       BEGIN
       ...
       END ]
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



<a name="loioa617091784f210158db2e43f0733ae5d__create_event_parm1"/>

## Parameters

 *<event-name\>*
 :   The event name is an identifier. An event has a creator, which is the user creating the event, and the event handler executes with the privileges of that creator. This is the same as stored procedure execution. You cannot create events owned by other users.

  *<user-name\>*
 :   Optionally, specify the name of a user in the system; when the event runs, it runs with the privileges of *<user-name\>*. If this parameter is not specified, the event runs with the privileges of the user who created the event. *<user-name\>* should not be confused with an owner of the event, however; events do not have owners.

  OR REPLACE clause
 :   Specifying OR REPLACE \(CREATE OR REPLACE EVENT\) creates an event or replaces an event with the same name. If the event already exists, then all comments are preserved when you use the OR REPLACE clause, but all existing attributes of the event are dropped.

  TYPE *<event-type\>*
 :   One of a set of system-defined event types. The event types are case-insensitive. To specify the conditions under which this *<event-type\>* triggers the event, use the WHERE clause.

     BackupEnd
     :   Take action at the end of a backup.

      Connect / ConnectFailed
     :   When a connection is made \(Connect\) or when a connection attempt fails \(ConnectFailed\), you may want to use these events for security purposes. As an alternative to a connect event handler, you may want to consider using a login procedure.

      DatabaseStart
     :   Take action when a database is started.

      Disconnect
     :   Take action when a user or application disconnects.

      Diskspace
     :   Tracks the available space on the device holding the database file \(DBDiskSpace\), the transaction log file \(LogDiskSpace\), or temporary file \(TempDiskSpace\).

        If the database contains an event handler for one of the DiskSpace types, the database server checks the available space on each device associated with the relevant file every 30 seconds.

        In the event the database has more than one dbspace, on separate drives, DBDiskSpace checks each drive and acts depending on the lowest available space.

        LogDiskSpace checks the location of the transaction log and any mirrored transaction log, and reports based on the least available space.

      File size
     :   Take action when the file reaches a specified size. This can be used for the database file \(GrowDB\), the transaction log \(GrowLog\), or the temporary file \(GrowTemp\).

        You may want to use file size events to track unusual actions on the database, or monitor bulk operations.

      GlobalAutoincrement
     :   When the number of remaining values for a column defined with GLOBAL AUTOINCREMENT is within one percent of its range, the GlobalAutoincrement event fires. A typical action for the handler could be to request a new value for the GLOBAL\_DATABASE\_ID clause.

        You can use the `EVENT_CONDITION` function with RemainingValues as an argument for this event type. RemainingValues returns the number of remaining values that can be generated for the column, while TableName returns the table containing the GLOBAL AUTOINCREMENT column that is near the end of its range.

      RAISERROR
     :   When a RAISERROR statement is executed, you can use the RAISERROR event type to take actions. The error number used in the RAISERROR statement can be determined within the event handler using the EVENT\_CONDITION function \(for example, `EVENT_CONDITION( 'ErrorNumber' )`\).

      ServerIdle
     :   If the database contains an event handler for the ServerIdle type, the server checks for server activity every 30 seconds.

   WHERE *<trigger-condition\>*
 :   The trigger condition determines the condition under which an event is fired. For example, to take an action when the storage space containing the transaction log becomes more than 80 percent full, use this triggering condition:

    ```
    ...
                  WHERE event_condition( 'LogDiskSpacePercentFree' ) < 20
                  ...
    ```

    The argument to the EVENT\_CONDITION function must be valid for the event type. You can use multiple AND conditions to make up the WHERE clause, but you cannot use OR conditions or other conditions.

    You can specify a variable name for the event\_condition value.

  SCHEDULE *<schedule-spec\>*
 :   Specifies when scheduled actions are to take place. The sequence of times acts as a set of triggering conditions for the associated actions defined in the event handler.You can create more than one schedule for a given event and its associated handler. This permits complex schedules to be implemented. While it is compulsory to provide a schedule name when there is more than one schedule, it is optional if you provide only a single schedule.

    You can list schedule names by querying the system table `SYSSCHEDULE`. For example:

    ```
    SELECT event_id, sched_name FROM SYS.SYSSCHEDULE
    ```

    Each event has a unique event ID. Use the `event_id` columns of `SYSEVENT` and `SYSSCHEDULE` to match the event to the associated schedule.

    When a nonrecurring scheduled event has passed, its schedule is deleted, but the event handler is not deleted.

    Scheduled event times are calculated when the schedules are created, and again when the event handler completes execution. The next event time is computed by inspecting the schedule or schedules for the event, and finding the next schedule time that is in the future. If an event handler is instructed to run every hour between 9:00 and 5:00, and it takes 65 minutes to execute, it runs at 9:00, 11:00, 1:00, 3:00, and 5:00. If you want execution to overlap, you must create more than one event.

    The subclauses of a schedule definition are as follows:

    -   START DATE – the date on which scheduled events are to start occurring. The default is the current date.
    -   START TIME – the first scheduled time for each day on which the event is scheduled. If a START DATE is specified, the START TIME refers to that date. If no START DATE is specified, the START TIME is on the current day \(unless the time has passed\) and each subsequent day.

        You can specify a variable name for *<start-time\>*.

    -   BETWEEN … AND – a range of times during the day outside of which no scheduled times occur. If a START DATE is specified, the scheduled times do not occur until that date.

        You can specify a variable name for *<start-time\>* and *<end-time\>*.

    -   EVERY – an interval between successive scheduled events. Scheduled events occur only after the START TIME for the day, or in the range specified by BETWEEN …AND.

        You can specify a variable name for *<period\>*.

    -   ON – a list of days on which the scheduled events occur. The default is every day. These can be specified as days of the week or days of the month.

        Days of the week are Monday, Tuesday, and so on. The abbreviated forms of the day, such as Mon, Tue, and so on, may also be used. The database server recognizes both full-length and abbreviated day names in any of the languages supported by data lake Relational Engine.

        Days of the month are integers from 0 to 31. A value of 0 represents the last day of any month.


    Each time a scheduled event handler is completed, the next scheduled time and date is calculated.

    -   If the EVERY clause is used, find whether the next scheduled time falls on the current day, and is before the end of the BETWEEN …AND range. If so, that is the next scheduled time.
    -   If the next scheduled time does not fall on the current day, find the next date on which the event is to be executed.
    -   Find the START TIME for that date, or the beginning of the BETWEEN … AND range.

  ENABLE | DISABLE
 :   By default, event handlers are enabled. When DISABLE is specified, the event handler does not execute even when the scheduled time or triggering condition occurs. A TRIGGER EVENT statement does not cause a disabled event handler to be executed

  AT \{ CONSOLIDATED | REMOTE | ALL \}
 :   To execute events at remote or consolidated databases in a SQL Remote setup, use this clause to restrict the databases at which the event is handled. By default, all databases execute the event.

  HANDLER
 :   Each event has one handler. Like the body of a stored procedure, the handler is a compound statement. There are some differences, though: you can use an EXCEPTION clause within the compound statement to handle errors, but not the ON EXCEPTION RESUME clause provided within stored procedures.

 

<a name="loioa617091784f210158db2e43f0733ae5d__create_event_remarks1"/>

## Remarks

An event definition includes two distinct pieces. The trigger condition can be an occurrence, such as a storage space filling up beyond a defined threshold. A schedule is a set of times, each of which acts as a trigger condition. When a trigger condition is satisfied, the event handler executes. The event handler includes one or more actions specified inside a compound statement \(`BEGIN... END`\).

If no trigger condition or schedule specification is supplied, only an explicit `TRIGGER EVENT` statement can trigger the event. During development, you might want to develop and test event handlers using `TRIGGER EVENT` and add the schedule or WHERE clause once testing is complete.

Event errors are logged to the database server console.

When event handlers are triggered, the server makes context information, such as the connection ID that caused the event to be triggered, available to the event handler using the `EVENT_PARAMETER` function.

> ### Note:  
> Although statements that return result sets are disallowed in events, you can allow an event to call a stored procedure and insert the procedure results into a temporary table.
> 
> For parameters that accept variable names, an error is returned if one of the following conditions is true:
> 
> -   The variable does not exist
> -   The contents of the variable are NULL
> -   The variable exceeds the length allowed by the parameter
> -   The data type of the variable does not match that required by the parameter



<a name="loioa617091784f210158db2e43f0733ae5d__IQ_Permissions"/>

## Privileges

To create or replace a self-owned event requires:

-   MANAGE EVENT system privilege

To create events owned by other users, requires one of:

-   MANAGE ANY EVENT system privilege
-   CREATE ANY OBJECT system privilege

To replace events owned by other users, requires one of:

-   MANAGE ANY EVENT system privilege
-   ALTER ANY OBJECT system privilege
-   CREATE ANY OBJECT and DROP ANY OBJECT system privileges

Event handlers execute on a separate connection, with the privileges of the event owner. To execute an event with privileges other than MANAGE ANY EVENT system privilege, you can call a procedure from within the event handler. The procedure executes with the permissions of its owner.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



<a name="loioa617091784f210158db2e43f0733ae5d__create_event_sideeffects1"/>

## Side Effects

-   Automatic commit.
-   The actions of an event handler are committed if no error is detected during execution, and rolled back if errors are detected.



<a name="loioa617091784f210158db2e43f0733ae5d__create_event_standards1"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loioa617091784f210158db2e43f0733ae5d__create_event_examples1"/>

## Examples

-   The following example instructs the database server to call the system stored procedure `sp_iqspaceused` every `10 minutes`, then store in a table the returned current date and time, the current number of connections to the database, and current information about the use of main and temporary IQ store:

    ```
    CREATE TABLE mysummary(dt DATETIME,
        users INT, mainKB UNSIGNED BIGINT,
        mainPC UNSIGNED INT,
        tempKB UNSIGNED BIGINT, 
        tempPC UNSIGNED INT) ;
    ```

    ```
    CREATE EVENT mysummary
        SCHEDULE sched_mysummary
            START TIME '00:01 AM' EVERY 10 MINUTES
        HANDLER
        BEGIN
            DECLARE mt UNSIGNED BIGINT;
            DECLARE mu UNSIGNED BIGINT;
            DECLARE tt UNSIGNED BIGINT;
            DECLARE tu UNSIGNED BIGINT;
            DECLARE conncount UNSIGNED INT;
                    
            SET conncount = DB_PROPERTY('ConnCount');
            CALL SP_IQSPACEUSED(mt,mu,tt,tu);
                    
            INSERT INTO mysummary VALUES( NOW(),
            conncount, mu, (mu*100)/mt, tu,
            (tu*100)/tt );
            COMMIT;
        END;
    
    ```

-   The following example posts a message to the server log when free disk space on the device containing the transaction log file falls below 30 percent, but execute the handler no more than once every 300 seconds:

    ```
    CREATE EVENT LowTxnLogDiskSpace
        TYPE DBDiskSpace
        WHERE event_condition( 'DBFreePercent' ) < 30  
        AND event_condition( 'Interval' ) >= 300
        HANDLER
        BEGIN 
            message 'Storage space for Transaction Log is low.';
        END;
    ```


**Related Information**  


[ALTER EVENT Statement for Data Lake Relational Engine](alter-event-statement-for-data-lake-relational-engine-a61251b.md "Changes the definition of an event or its associated handler for automating predefined actions. Also alters the definition of scheduled actions.")

[BEGIN … END Statement for Data Lake Relational Engine](begin-end-statement-for-data-lake-relational-engine-a6142de.md "Groups SQL statements together.")

[COMMENT Statement for Data Lake Relational Engine](comment-statement-for-data-lake-relational-engine-a615ad2.md "Stores a comment, in the system tables, about a database object.")

[DROP Statement for Data Lake Relational Engine](drop-statement-for-data-lake-relational-engine-a61c216.md "Removes objects from the database.")

[TRIGGER EVENT Statement for Data Lake Relational Engine](trigger-event-statement-for-data-lake-relational-engine-a627b6f.md "Triggers a named event. The event may be defined for event triggers or be a scheduled event.")

[EVENT\_CONDITION Function \[System\] for Data Lake Relational Engine](../050-system-sql-functions/event-condition-function-system-for-data-lake-relational-engine-a54fb34.md "Specifies when an event handler is triggered.")

[EVENT\_CONDITION\_NAME Function \[System\] for Data Lake Relational Engine](../050-system-sql-functions/event-condition-name-function-system-for-data-lake-relational-engine-a550344.md "Can be used to list the possible parameters for EVENT_CONDITION.")

[EVENT\_PARAMETER Function \[System\] for Data Lake Relational Engine](../050-system-sql-functions/event-parameter-function-system-for-data-lake-relational-engine-a550b30.md "Provides context information for event handlers.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

