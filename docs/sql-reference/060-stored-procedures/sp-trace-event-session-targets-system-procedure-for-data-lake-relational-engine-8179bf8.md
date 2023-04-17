<!-- loio8179bf806ce210148693c5362783c940 -->

# sp\_trace\_event\_session\_targets System Procedure for Data Lake Relational Engine

Lists the targets of a trace session.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_trace_event_session_targets(
   [ <session_name>  
   [, <include_server_sessions>
   [, <include_audit_events> ] ] ]
)
```



<a name="loio8179bf806ce210148693c5362783c940__sp_trace_event_session_targets_parm1"/>

## Parameters

  *<session\_name\>* 
 :   Use this optional CHAR\(256\) parameter to specify the name of the trace event session. The default is NULL. If a session name is not specified or is NULL, information is returned about all trace event sessions in the database.

   *<include\_server\_sessions\>* 
 :   Use this optional BIT parameter to specify whether or not engine-level trace event sessions are returned. This parameter can be 0 \(do not return engine-level trace event sessions\) or 1 \(return engine-level trace event sessions\). The default is 0.

   *<include\_audit\_events\>* 
 :   Use this optional BIT parameter to specify whether or not audit events are returned. This parameter can be 0 \(do not return audit events\) or 1 \(return audit events\). The default is 0.

 

<a name="loio8179bf806ce210148693c5362783c940__sp_trace_event_session_targets_resultset1"/>

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

Returns the target type \(for example, a file\).



</td>
</tr>
</table>



<a name="loio8179bf806ce210148693c5362783c940__sp_trace_event_session_targets_remarks1"/>

## Remarks

A target is the location where the trace event session information is being logged \(such as a file or database server message log\).



## Privileges

You need to have the EXECUTE privilege on the system procedure, as well as the MANAGE ANY TRACE SESSION system privilege. You also need the MANAGE AUDITING system privilege if *<include\_audit\_events\>* isn’t set.



<a name="loio8179bf806ce210148693c5362783c940__sp_trace_event_session_targets_sideeffects1"/>

## Side Effects

None.



The following statement returns information about all trace event sessions in the database:

```
SELECT * FROM dbo.sp_trace_event_session_targets( );
```

**Related Information**  


[sp_trace_event_session_targets System Procedure for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/08a49c4ce49d4d44b534b74d5e9aac35.html "Lists the targets of a trace session.") :arrow_upper_right:

