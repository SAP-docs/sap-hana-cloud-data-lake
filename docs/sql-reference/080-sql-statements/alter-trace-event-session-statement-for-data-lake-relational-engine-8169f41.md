<!-- loio8169f4176ce21014b768e5f2b0bf8951 -->

# ALTER TRACE EVENT SESSION Statement for Data Lake Relational Engine

Adds or removes trace events or targets from a session, or starts or stops a trace session.



<a name="loio8169f4176ce21014b768e5f2b0bf8951__section_azh_5fj_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
ALTER TRACE EVENT SESSION <session-name> 
[ ON SERVER ]    
{ ADD TRACE EVENT <trace-event-name> [,...]  
  | DROP TRACE EVENT <trace-event-name> [,...]
  | ADD TARGET FILE [ ( SET <target-parameter-name>=<target-parameter-value> [, ...] ) ]
  | DROP TARGET <FILE> [, ...] ]
  | STATE = { START | STOP }
}
```

```
<target-parameter-name> :
{ filename_prefix
 | flush_on_write
 | compressed }
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio8169f4176ce21014b768e5f2b0bf8951__alter_trace_parameter1"/>

## Parameters


<dl class="glossary">
<dt><b>

ON SERVER clause

</b></dt>
<dd>

Alters a trace event session that is recording trace events from all databases on the database server. If this clause is not specified, then only the trace event session on the current database is altered.



</dd><dt><b>

ADD TRACE EVENT

</b></dt>
<dd>

The name of the trace event being added to the session.


<dl>
<dt><b>

*<trace-event-name\>*

</b></dt>
<dd>

The name of the trace event in the session. System- and user-defined trace events are supported. Call the sp\_trace\_events system procedure to obtain a list of system-defined trace events.



</dd>
</dl>



</dd><dt><b>

DROP TRACE EVENT

</b></dt>
<dd>

The name of the trace event being removed from the session.



</dd><dt><b>

ADD TARGET FILE

</b></dt>
<dd>

The name of the target being added to the session. Information about the trace events that are part of the session is logged to this target \(file\).



</dd><dt><b>

DROP TARGET FILE

</b></dt>
<dd>

The name of the target being removed from the session.



</dd><dt><b>

STATE

</b></dt>
<dd>

Either START or STOP. Start a trace session so that event tracing information is recorded to ETD files. Once started, the session runs until you explicitly stop the trace session, or until the instance is stopped.



</dd><dt><b>

ADD TARGET TILE

</b></dt>
<dd>


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



<a name="loio8169f4176ce21014b768e5f2b0bf8951__alter_trace_remarks1"/>

## Remarks

Adding or dropping trace events or targets from a running trace session causes the session to pause briefly to make the changes and then resume after the changes are made. You do not need to stop a tracing session to add or drop trace events or targets. Adding or removing a trace event from a session that has already started has the side effect that some trace events are missed while a session is temporarily paused.



<a name="loio8169f4176ce21014b768e5f2b0bf8951__alter_trace_privileges1"/>

## Privileges

You have the MANAGE ANY TRACE SESSION system privilege.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



<a name="loio8169f4176ce21014b768e5f2b0bf8951__alter_trace_side_effects1"/>

## Side Effects

None



<a name="loio8169f4176ce21014b768e5f2b0bf8951__alter_trace_standards1"/>

## Standards


<dl>
<dt><b>

ANSI/ISO SQL Standard

</b></dt>
<dd>

Not in the standard.



</dd>
</dl>



<a name="loio8169f4176ce21014b768e5f2b0bf8951__alter_trace_examples1"/>

## Examples

The following example creates a trace event called my\_event, a trace event session called my\_session, and then alters the session to start it:

```
CREATE OR REPLACE TEMPORARY TRACE EVENT my_event( id INTEGER, information LONG VARCHAR );

CREATE OR REPLACE TEMPORARY TRACE EVENT SESSION my_session
   ADD TRACE EVENT my_event,
   ADD TRACE EVENT SYS_ConsoleLog_Information
   ADD TARGET FILE ( SET filename_prefix='my_trace_file' );
```

```
ALTER TRACE EVENT SESSION my_session STATE = START;
```

**Related Information**  


[CREATE TEMPORARY TRACE EVENT SESSION Statement for Data Lake Relational Engine](create-temporary-trace-event-session-statement-for-data-lake-relational-engine-816cf4d.md "Creates a user trace event session.")

[DROP TRACE EVENT SESSION Statement for Data Lake Relational Engine](drop-trace-event-session-statement-for-data-lake-relational-engine-816f77f.md "Drops a trace event session.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[ALTER TRACE EVENT SESSION Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/21b2b4f214224d81920ed9bcaf88d7ee.html "Adds or removes trace events or targets from a session, or starts or stops a trace session.") :arrow_upper_right:

