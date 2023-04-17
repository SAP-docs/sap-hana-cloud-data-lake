<!-- loio8179a2a56ce210148a18fd12322fa8f2 -->

# sp\_trace\_event\_fields System Procedure for Data Lake Relational Engine

Returns information about the fields of the specified trace event.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_trace_event_fields( 
   [ <event_name> 
   [, <include_audit_events> ] ]
  )
```



<a name="loio8179a2a56ce210148a18fd12322fa8f2__sp_trace_event_fields_parm1"/>

## Parameters

  *<event\_name\>* 
 :   Use this optional CHAR\(256\) parameter to specify the trace event name. The default is NULL.

   *<include\_audit\_events\>* 
 :   Use this optional BIT parameter to specify whether or not audit events are returned. This parameter can be 0 \(do not return audit events\) or 1 \(return audit events\). By default, audit events are not returned \(0 is the default\).

 

<a name="loio8179a2a56ce210148a18fd12322fa8f2__sp_trace_event_fields_resultset1"/>

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

event\_name



</td>
<td valign="top">

CHAR\(256\)



</td>
<td valign="top">

Returns the name of the trace event.



</td>
</tr>
<tr>
<td valign="top">

field\_name



</td>
<td valign="top">

CHAR\(256\)



</td>
<td valign="top">

Returns the field name.



</td>
</tr>
<tr>
<td valign="top">

field\_id



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Returns the order of the field in the trace event.



</td>
</tr>
<tr>
<td valign="top">

field\_domain



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Returns the domain ID of the field. Foreign key to SYSDOMAIN.domain\_id.



</td>
</tr>
<tr>
<td valign="top">

field\_description



</td>
<td valign="top">

LONG VARCHAR



</td>
<td valign="top">

Returns a description of the field content.



</td>
</tr>
</table>



<a name="loio8179a2a56ce210148a18fd12322fa8f2__sp_trace_event_fields_remarks1"/>

## Remarks

If *<event\_name\>* is NULL, this procedure returns the fields for all trace events.



## Privileges

You need to have the EXECUTE privilege on the system procedure, as well as the MANAGE ANY TRACE SESSION system privilege. You'll also need the MANAGE AUDITING system privilege if *<include\_audit\_events\>* isn’t set.



<a name="loio8179a2a56ce210148a18fd12322fa8f2__sp_trace_event_fields_sideeffects1"/>

## Side Effects

None.



The following statement returns information about the fields for all trace event sessions in the database:

```
SELECT * FROM dbo.sp_trace_event_fields( );
```

**Related Information**  


[sp_trace_event_fields System Procedure for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/301a2c803cd847d8a5eec27d96cff484.html "Returns information about the fields of the specified trace event.") :arrow_upper_right:

