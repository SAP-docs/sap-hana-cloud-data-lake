<!-- loio816cf4d46ce2101485eddafc5b7ce186 -->

# CREATE TEMPORARY TRACE EVENT SESSION Statement for Data Lake Relational Engine

Creates a user trace event session.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
CREATE [ OR REPLACE ] TEMPORARY TRACE EVENT SESSION <session-name> 
<event-definition> [ ,... ]
[ <target-definition> ]
```

```
<event-definition> :
ADD TRACE EVENT <trace-event-name> [ ( WHERE <search-condition> ) ]
```

```
<target-definition> :
ADD TARGET FILE
  ( SET <target-parameter-name>=<target-parameter-value> [ ,... ] )
```

```
<target-parameter-name> :
{ filename_prefix
 | flush_on_write
 | ["compressed"] }
```



<a name="loio816cf4d46ce2101485eddafc5b7ce186__create_temp_trace_event_sess_parameters1"/>

## Parameters

 OR REPLACE clause
 :   Specifying CREATE OR REPLACE creates a trace event session or replaces an existing trace event session with the same name.

  WHERE clause
 :   The WHERE clause allows an event to be traced conditionally based on its properties, and can contain expressions that refer to constants and event fields. If there are built-in functions used in *<search-condition\>*, then they are evaluated on the connection generating the event. For example, using `connection_property('number') = 101` logs only events for connections with the number 101.

    *<search-condition\>* is applied before events are sent to *<target-definition\>*. If *<search-condition\>* returns FALSE \(or UNKNOWN\), then the event is not sent to the target.

    *<search-condition\>* returns an error if it contains any of the following:

    -   Sub-queries

    -   User-defined functions

    -   Sequences

    -   Host variables

    -   Column references \(may refer to fields of the event but not WHERE clause of the event\)

    -   Connection or database variables


   *<session-name\>* 
 :   The name of the trace event session.

   *<trace-event-name\>* 
 :   The name of the trace event in the session. System- and user-defined trace events are supported. Call the sp\_trace\_events system procedure to obtain a list of system-defined trace events.

   *<target-parameter-name\>* 
 :   The following target parameters are supported:


    <table>
    <tr>
    <th valign="top">

     *<target-parameter-name\>* 


    
    </th>
    <th valign="top">

     *<target-parameter-value\>* 


    
    </th>
    </tr>
    <tr>
    <td valign="top">

    filename\_prefix


    
    </td>
    <td valign="top">

    \(Required\) An ETD file name prefix with or without a path. ETD files have the extension `.etd`.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    flush\_on\_write


    
    </td>
    <td valign="top">

    A boolean \(true or false\) value that controls whether disk buffers are flushed for each event that is logged. The default is false. When flushing is enabled, the performance of the database server may be reduced if many trace events are being logged.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    \[compressed\]


    
    </td>
    <td valign="top">

    A boolean \(true or false\) value that controls compression of the ETD file to conserve disk space. The default is false. Use brackets with this parameter name because it is a keyword in other contexts.


    
    </td>
    </tr>
    </table>
    
 

<a name="loio816cf4d46ce2101485eddafc5b7ce186__create_temp_trace_event_sess_remarks1"/>

## Remarks

Trace event sessions do not run until they are explicitly started with the ALTER TRACE EVENT SESSION statement. Trace event sessions capture trace events related to system behavior or for a particular user. Trace event sessions are stored in memory and are dropped when the database server stops if they have not been dropped explicitly.



<a name="loio816cf4d46ce2101485eddafc5b7ce186__create_temp_trace_event_priv1"/>

## Privileges



### 

You have the MANAGE ANY TRACE SESSION system privilege.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



<a name="loio816cf4d46ce2101485eddafc5b7ce186__create_temp_trace_event_sess_side_effects1"/>

## Side Effects

None



<a name="loio816cf4d46ce2101485eddafc5b7ce186__create_temp_trace_event_sess_standards1"/>

## Standards

 ANSI/ISO SQL Standard
 :   Not in the standard.

 

The following statement creates an event tracing session that records information about the user-defined event my\_event and the system-defined event SYS\_ConsoleLog\_Information to a file named `my_trace_file`:

```
CREATE TEMPORARY TRACE EVENT SESSION my_session
    ADD TRACE EVENT my_event -- user event
    ADD TRACE EVENT SYS_ConsoleLog_Information -- system event
    ADD TARGET FILE (SET filename_prefix='my_trace_file', [compressed]=1); -- add a target
```

The following statement creates an event tracing session called MySession that records connection events for user HDLADMIN:

```
CREATE TEMPORARY TRACE EVENT SESSION MySession 

ADD TRACE EVENT SYS_RLL_Connect 

( WHERE user='HDLADMIN' );
```

**Related Information**  


[CREATE TEMPORARY TRACE EVENT SESSION Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/0c1bc711bafd418da40a48480179d22e.html "Creates a user trace event session.") :arrow_upper_right:

[DROP TRACE EVENT SESSION Statement for Data Lake Relational Engine](drop-trace-event-session-statement-for-data-lake-relational-engine-816f77f.md "Drops a trace event session.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")
