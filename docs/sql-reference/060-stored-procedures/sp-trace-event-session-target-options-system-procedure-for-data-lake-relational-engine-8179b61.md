<!-- loio8179b61a6ce210148e4db24e40891e7d -->

# sp\_trace\_event\_session\_target\_options System Procedure for Data Lake Relational Engine

Lists the target options for a trace event session.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_trace_event_session_target_options(
   [ <session_name>  
   [, <include_server_sessions>
   [, <include_audit_events> ] ] ]
  )
```



<a name="loio8179b61a6ce210148e4db24e40891e7d__sp_trace_event_session_target_options_parm1"/>

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



<a name="loio8179b61a6ce210148e4db24e40891e7d__sp_trace_event_session_target_options_resultset1"/>

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

Returns the session name.



</td>
</tr>
<tr>
<td valign="top">

target\_type



</td>
<td valign="top">

CHAR\(256\)



</td>
<td valign="top">

Returns the target type.



</td>
</tr>
<tr>
<td valign="top">

option\_name



</td>
<td valign="top">

CHAR\(256\)



</td>
<td valign="top">

Returns the option name.



</td>
</tr>
<tr>
<td valign="top">

option\_value



</td>
<td valign="top">

LONG VARCHAR



</td>
<td valign="top">

Returns the option value.



</td>
</tr>
</table>



<a name="loio8179b61a6ce210148e4db24e40891e7d__sp_trace_event_session_target_options_remarks1"/>

## Remarks

This procedure returns option information for one, or all, trace event sessions for the current database.



<a name="loio8179b61a6ce210148e4db24e40891e7d__sp_trace_event_session_target_options_priv1"/>

## Privileges



### 

Requires all of the following:

-   EXECUTE object-level privilege on the procedure
-   MANAGE ANY TRACE SESSION system privilege
-   MANAGE AUDITING system privilege



<a name="loio8179b61a6ce210148e4db24e40891e7d__sp_trace_event_session_target_options_sideeffects1"/>

## Side Effects

None.



The following statement returns information about target options for all trace event sessions in the database:

```
SELECT * FROM dbo.sp_trace_event_session_target_options( );
```

**Related Information**  


[sp_trace_event_session_target_options System Procedure for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/aae165896e5d4689b72835021f67795e.html "Lists the target options for a trace event session.") :arrow_upper_right:

