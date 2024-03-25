<!-- loio8179ac5d6ce210149cfcd3fb6d77cbca -->

# sp\_trace\_event\_session\_events System Procedure for Data Lake Relational Engine

Lists the trace events that are part of a specific trace event session.



<a name="loio8179ac5d6ce210149cfcd3fb6d77cbca__section_p4t_vqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_trace_event_session_events(
   [ <event_name> 
   [, <include_server_sessions>
   [, <include_audit_events> ] ] ]
  )
```



<a name="loio8179ac5d6ce210149cfcd3fb6d77cbca__sp_trace_event_session_events_parm1"/>

## Parameters


<dl>
<dt><b>

*<session\_name\>* 

</b></dt>
<dd>

Use this optional CHAR\(256\) parameter to specify the name of the trace event session. The default is NULL. If a session name is not specified or is NULL, information is returned for all trace event sessions.



</dd><dt><b>

*<include\_server\_sessions\>* 

</b></dt>
<dd>

Use this optional BIT parameter to specify whether or not engine-level trace event sessions are returned. This parameter can be 0 \(do not return engine-level trace event sessions\) or 1 \(return engine-level trace event sessions\). The default is 0.



</dd><dt><b>

*<include\_audit\_events\>* 

</b></dt>
<dd>

Use this optional BIT parameter to specify whether or not audit events are returned. This parameter can be 0 \(do not return audit events\) or 1 \(return audit events\). The default is 0.



</dd>
</dl>



<a name="loio8179ac5d6ce210149cfcd3fb6d77cbca__sp_trace_event_session_events_resultset1"/>

## Result Set


<table>
<tr>
<th valign="top">

Column name

</th>
<th valign="top">

Data type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

session\_name

</td>
<td valign="top">

CHAR\(256\)

</td>
<td valign="top">

Returns the name of the trace event session.

</td>
</tr>
<tr>
<td valign="top">

event\_name

</td>
<td valign="top">

CHAR\(256\)

</td>
<td valign="top">

Returns the trace event name.

</td>
</tr>
</table>



<a name="loio8179ac5d6ce210149cfcd3fb6d77cbca__sp_trace_event_session_events_remarks1"/>

## Remarks

Use this system procedure to determine which trace events \(both system defined and user defined\) are being logged for a trace event session.



<a name="loio8179ac5d6ce210149cfcd3fb6d77cbca__sp_trace_event_session_events_priv1"/>

## Privileges



### 

Requires all of the following:

-   EXECUTE object-level privilege on the procedure
-   MANAGE ANY TRACE SESSION system privilege
-   MANAGE AUDITING system privilege



<a name="loio8179ac5d6ce210149cfcd3fb6d77cbca__sp_trace_event_session_events_sideeffects1"/>

## Side Effects

None.



## Example

This statement returns information about the events that are part of all the event tracing sessions for the current database:

```
CALL sp_trace_event_session_events( );
```

**Related Information**  


[sp_trace_event_session_events System Procedure for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/f906a7948fa14abcadfd72ef71b410f7.html "Lists the trace events that are part of a specific trace event session.") :arrow_upper_right:

