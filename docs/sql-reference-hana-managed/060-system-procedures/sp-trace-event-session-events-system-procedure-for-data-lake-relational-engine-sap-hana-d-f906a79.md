<!-- loiof906a7948fa14abcadfd72ef71b410f7 -->

# sp\_trace\_event\_session\_events System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Lists the trace events that are part of a specific trace event session.



<a name="loiof906a7948fa14abcadfd72ef71b410f7__section_tv3_scb_1yb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) system procedure can be used when:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.

> ### Restriction:  
> This syntax cannot be run when connected to SAP HANA database as a SAP HANA database user and using SAP HANA database REMOTE\_EXECUTE or REMOTE\_EXECUTE\_QUERY.



```
sp_trace_event_session_events(
   [ <event_name> 
   [, <include_server_sessions>
   [, <include_audit_events> ] ] ]
  )
```



<a name="loiof906a7948fa14abcadfd72ef71b410f7__section_jjr_jn2_srb"/>

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



<a name="loiof906a7948fa14abcadfd72ef71b410f7__section_kkh_kn2_srb"/>

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



<a name="loiof906a7948fa14abcadfd72ef71b410f7__section_p3v_kn2_srb"/>

## Remarks

Use this system procedure to determine which trace events \(both system defined and user defined\) are being logged for a trace event session.



<a name="loiof906a7948fa14abcadfd72ef71b410f7__section_frd_xcb_1yb"/>

## Privileges



### 


<dl>
<dt><b>

Connected directly to data lake Relational Engine as a data lake Relational Engine user:

</b></dt>
<dd>

Requires all of the following:

-   EXECUTE object-level privilege on the procedure
-   MANAGE ANY TRACE SESSION system privilege
-   MANAGE AUDITING system privilege



</dd>
</dl>



<a name="loiof906a7948fa14abcadfd72ef71b410f7__section_hwm_ln2_srb"/>

## Side Effects

None.



## Example

This statement returns information about the events that are part of all the event tracing sessions for the current database:

```
CALL sp_trace_event_session_events( );
```

**Related Information**  


[sp_trace_event_session_events System Procedure for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/8179ac5d6ce210149cfcd3fb6d77cbca.html "Lists the trace events that are part of a specific trace event session.") :arrow_upper_right:

