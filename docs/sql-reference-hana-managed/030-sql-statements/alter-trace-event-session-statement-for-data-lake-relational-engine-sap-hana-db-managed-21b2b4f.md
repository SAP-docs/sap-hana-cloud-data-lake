<!-- loio21b2b4f214224d81920ed9bcaf88d7ee -->

# ALTER TRACE EVENT SESSION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Adds or removes trace events or targets from a session, or starts or stops a trace session.



<a name="loio21b2b4f214224d81920ed9bcaf88d7ee__section_kyf_nhw_ysb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:

-   Connected directly to data lake Relational Engine **coordinator** as a data lake Relational Engine user. This syntax cannot be run using the REMOTE\_EXECUTE procedure.



```
ALTER TRACE EVENT SESSION <session-name> 
[ ON SERVER ]    
{ ADD TRACE EVENT <trace-event-name> [,...]  
  | DROP TRACE EVENT <trace-event-name> [,...]
  | ADD TARGET FILE [ ( SET <target-parameter-name>=<target-parameter-value> [, ...] ) ]
  | DROP TARGET <FILE> [, ...] ]
  | STATE = { START | STOP }
};
```

```
<target-parameter-name> :
{ filename_prefix
 | flush_on_write
 | compressed };
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio21b2b4f214224d81920ed9bcaf88d7ee__section_hky_zlg_1rb"/>

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
{ filename_prefix
 | flush_on_write
 | ["compressed"] };
```

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



</dd>
</dl>



<a name="loio21b2b4f214224d81920ed9bcaf88d7ee__section_djb_bmg_1rb"/>

## Remarks

Adding or dropping trace events or targets from a running trace session causes the session to pause briefly to make the changes and then resume after the changes are made. You do not need to stop a tracing session to add or drop trace events or targets. Adding or removing a trace event from a session that has already started has the side effect that some trace events are missed while a session is temporarily paused.



<a name="loio21b2b4f214224d81920ed9bcaf88d7ee__section_iwd_bfq_wwb"/>

## Privileges

You have the MANAGE ANY TRACE SESSION system privilege.



<a name="loio21b2b4f214224d81920ed9bcaf88d7ee__section_mqv_bmg_1rb"/>

## Side Effects

None



<a name="loio21b2b4f214224d81920ed9bcaf88d7ee__section_kb3_cmg_1rb"/>

## Standards


<dl>
<dt><b>

ANSI/ISO SQL Standard

</b></dt>
<dd>

Not in the standard.



</dd>
</dl>



## Example

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


[ALTER TRACE EVENT SESSION Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/8169f4176ce21014b768e5f2b0bf8951.html "Adds or removes trace events or targets from a session, or starts or stops a trace session.") :arrow_upper_right:

[CREATE TEMPORARY TRACE EVENT SESSION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](create-temporary-trace-event-session-statement-for-data-lake-relational-engine-sap-hana-d-0c1bc71.md "Creates a user trace event session.")

[DROP TRACE EVENT SESSION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](drop-trace-event-session-statement-for-data-lake-relational-engine-sap-hana-db-managed-1b596ab.md "Drops a trace event session.")

