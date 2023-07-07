<!-- loio8169f4176ce21014b768e5f2b0bf8951 -->

# ALTER TRACE EVENT SESSION Statement for Data Lake Relational Engine

Adds or removes trace events or targets from a session, or starts or stops a trace session.



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



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

 *<trace-event-name\>* 

</b></dt>
<dd>

The name of the trace event in the session. System- and user-defined trace events are supported. Call the sp\_trace\_events system procedure to obtain a list of system-defined trace events.



</dd><dt><b>

ADD TRACE EVENT

</b></dt>
<dd>

The name of the trace event being added to the session.



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

 *<target-parameter-name\>* 

</b></dt>
<dd>

The following target parameters are supported:


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



The following example creates a trace event called my\_event, a trace event session called my\_session, and starts the session:

```
CREATE TEMPORARY TRACE EVENT my_event( id INTEGER, information LONG VARCHAR );
CREATE TEMPORARY TRACE EVENT SESSION my_session
    ADD TRACE EVENT my_event, -- user event
    ADD TRACE EVENT SYS_ConsoleLog_Information -- system event
    ADD TARGET FILE ( SET filename_prefix='my_trace_file' ); -- add a target
ALTER TRACE EVENT SESSION my_session
     STATE = START;
```

**Related Information**  


[CREATE TEMPORARY TRACE EVENT SESSION Statement for Data Lake Relational Engine](create-temporary-trace-event-session-statement-for-data-lake-relational-engine-816cf4d.md "Creates a user trace event session.")

[DROP TRACE EVENT SESSION Statement for Data Lake Relational Engine](drop-trace-event-session-statement-for-data-lake-relational-engine-816f77f.md "Drops a trace event session.")

[ALTER TRACE EVENT SESSION Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/21b2b4f214224d81920ed9bcaf88d7ee.html "Adds or removes trace events or targets from a session, or starts or stops a trace session.") :arrow_upper_right:

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

