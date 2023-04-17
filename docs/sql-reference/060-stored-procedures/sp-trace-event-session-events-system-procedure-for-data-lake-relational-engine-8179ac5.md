<!-- loio8179ac5d6ce210149cfcd3fb6d77cbca -->

# sp\_trace\_event\_session\_events System Procedure for Data Lake Relational Engine

Lists the trace events that are part of a specific trace event session.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_trace_event_session_events(
   [ <event_name> 
   [, <include_server_sessions>
   [, <include_audit_events> ] ] ]
  )
```



<a name="loio8179ac5d6ce210149cfcd3fb6d77cbca__sp_trace_event_session_events_parm1"/>

## Parameters

  *<session\_name\>* 
 :   Use this optional CHAR\(256\) parameter to specify the name of the trace event session. The default is NULL. If a session name is not specified or is NULL, information is returned for all trace event sessions.

   *<include\_server\_sessions\>* 
 :   Use this optional BIT parameter to specify whether or not engine-level trace event sessions are returned. This parameter can be 0 \(do not return engine-level trace event sessions\) or 1 \(return engine-level trace event sessions\). The default is 0.

   *<include\_audit\_events\>* 
 :   Use this optional BIT parameter to specify whether or not audit events are returned. This parameter can be 0 \(do not return audit events\) or 1 \(return audit events\). The default is 0.

 

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



## Privileges

You need to have the EXECUTE privilege on the system procedure, as well as the MANAGE ANY TRACE SESSION system privilege. You'll also need the MANAGE AUDITING system privilege if *<include\_audit\_events\>* isn’t set.



<a name="loio8179ac5d6ce210149cfcd3fb6d77cbca__sp_trace_event_session_events_sideeffects1"/>

## Side Effects

None.



This statement returns information about the events that are part of all the event tracing sessions for the current database:

```
SELECT * FROM dbo.sp_trace_event_session_events( );
```

**Related Information**  


[sp_trace_event_session_events System Procedure for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/f906a7948fa14abcadfd72ef71b410f7.html "Lists the trace events that are part of a specific trace event session.") :arrow_upper_right:
