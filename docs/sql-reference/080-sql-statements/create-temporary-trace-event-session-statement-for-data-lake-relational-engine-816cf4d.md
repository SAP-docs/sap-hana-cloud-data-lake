<!-- loio816cf4d46ce2101485eddafc5b7ce186 -->

# CREATE TEMPORARY TRACE EVENT SESSION Statement for Data Lake Relational Engine

Creates a user trace event session.



<a name="loio816cf4d46ce2101485eddafc5b7ce186__section_azh_5fj_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
CREATE [ OR REPLACE ] TEMPORARY TRACE EVENT SESSION <session-name> 
   <event-definition> [ ,... ]
   [ <target-definition> ]
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio816cf4d46ce2101485eddafc5b7ce186__create_temp_trace_event_sess_parameters1"/>

## Parameters


<dl class="glossary">
<dt><b>

OR REPLACE clause

</b></dt>
<dd>

Specifying CREATE OR REPLACE creates a trace event session or replaces an existing trace event session with the same name.



</dd><dt><b>

WHERE clause

</b></dt>
<dd>

The WHERE clause allows an event to be traced conditionally based on its properties, and can contain expressions that refer to constants and event fields. If there are built-in functions used in *<search-condition\>*, then they are evaluated on the connection generating the event. For example, using `connection_property('number') = 101` logs only events for connections with the number 101.

*<search-condition\>* is applied before events are sent to *<target-definition\>*. If *<search-condition\>* returns FALSE \(or UNKNOWN\), then the event is not sent to the target.

*<search-condition\>* returns an error if it contains any of the following:

-   Sub-queries

-   User-defined functions

-   Sequences

-   Host variables

-   Column references \(may refer to fields of the event but not WHERE clause of the event\)

-   Connection or database variables




</dd><dt><b>

*<session-name\>* 

</b></dt>
<dd>

The name of the trace event session.



</dd><dt><b>

*<event-definition\>*

</b></dt>
<dd>

Add trace events to the session.

```
<event-definition> ::=
   ADD TRACE EVENT <trace-event-name> [ ( WHERE <search-condition> ) ]
```


<dl>
<dt><b>

*<trace-event-name\>*

</b></dt>
<dd>

The name of the trace event in the session. System- and user-defined trace events are supported. Call the sp\_trace\_events system procedure to obtain a list of system-defined trace events.



</dd>
</dl>



</dd><dt><b>

*<target-definition\>*

</b></dt>
<dd>

Adds the target file to the trace event session definition.

```
<target-definition> :
   ADD TARGET FILE ( SET <target-parameter-name> [,... ] )
```


<dl>
<dt><b>

*<target-parameter-name\>*

</b></dt>
<dd>

```
<target-parameter-name> :
{ filename_prefix = <path-and-filename>
 | flush_on_write = = { ON | OFF }
 | ["compressed"] = = { ON | OFF }
```


<dl>
<dt><b>

filename\_prefix

</b></dt>
<dd>

A log file name prefix with or without a path. All log files have the extension `.etd`. If a full path is not specified, then the directory where the database is located is used as the root directory.



</dd><dt><b>

flush\_on\_write

</b></dt>
<dd>

A Boolean value that controls whether disk buffers are flushed for each event that is logged. The default is ON. When this parameter is turned on, the performance of the database server may be reduced if many trace events are being logged.



</dd><dt><b>

compressed

</b></dt>
<dd>

A Boolean value that controls compression of the log file to conserve disk space. The default is OFF.



</dd>
</dl>

The following target parameters are supported:



</dd>
</dl>



</dd>
</dl>



<a name="loio816cf4d46ce2101485eddafc5b7ce186__create_temp_trace_event_sess_remarks1"/>

## Remarks

Trace event sessions do not run until they are explicitly started with the ALTER TRACE EVENT SESSION statement. Trace event sessions capture trace events related to system behavior or for a particular user. Trace event sessions are stored in memory and are dropped when the database server stops if they have not been dropped explicitly.



<a name="loio816cf4d46ce2101485eddafc5b7ce186__create_temp_trace_event_priv1"/>

## Privileges

You have the MANAGE ANY TRACE SESSION system privilege.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



<a name="loio816cf4d46ce2101485eddafc5b7ce186__create_temp_trace_event_sess_side_effects1"/>

## Side Effects

None



<a name="loio816cf4d46ce2101485eddafc5b7ce186__create_temp_trace_event_sess_standards1"/>

## Standards


<dl>
<dt><b>

ANSI/ISO SQL Standard

</b></dt>
<dd>

Not in the standard.



</dd>
</dl>



<a name="loio816cf4d46ce2101485eddafc5b7ce186__create_temp_trace_event_sess_example1"/>

## Examples

The following statement creates a trace event called my\_event, and then creates a trace event session that records information about the user-defined event my\_event and the system-defined event SYS\_ConsoleLog\_Information to a file named my\_trace\_file.

```
CREATE OR REPLACE TEMPORARY TRACE EVENT my_event( id INTEGER, information LONG VARCHAR );

CREATE TEMPORARY TRACE EVENT SESSION my_session
    ADD TRACE EVENT my_event,
    ADD TRACE EVENT SYS_ConsoleLog_Information
    ADD TARGET FILE (SET filename_prefix='my_trace_file', [compressed]=1); -- add a target;
```

The following statement creates an event tracing session called my\_session\_hdladmin that records connection events for user HDLADMIN:

```
CREATE OR REPLACE TEMPORARY TRACE EVENT SESSION my_session_hdladmin ADD TRACE EVENT SYS_RLL_Connect 
   ( WHERE user='HDLADMIN' );
```

**Related Information**  


[CREATE TEMPORARY TRACE EVENT SESSION Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/0c1bc711bafd418da40a48480179d22e.html "Creates a user trace event session.") :arrow_upper_right:

[DROP TRACE EVENT SESSION Statement for Data Lake Relational Engine](drop-trace-event-session-statement-for-data-lake-relational-engine-816f77f.md "Drops a trace event session.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[sp\_trace\_events System Procedure for Data Lake Relational Engine](../060-stored-procedures/sp-trace-events-system-procedure-for-data-lake-relational-engine-8179d29.md "Returns information about the trace events in the database.")

