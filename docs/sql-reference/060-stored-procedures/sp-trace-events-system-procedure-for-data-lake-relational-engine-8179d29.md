<!-- loio8179d2976ce210148418a9a15900e7e2 -->

# sp\_trace\_events System Procedure for Data Lake Relational Engine

Returns information about the trace events in the database.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_trace_events(
   [ <event_name> 
   [, <include_audit_events> ] ]
)
```



<a name="loio8179d2976ce210148418a9a15900e7e2__sp_trace_events_parm"/>

## Parameters


<dl>
<dt><b>

 *<event\_name\>* 

</b></dt>
<dd>

Use this optional CHAR\(256\) parameter to specify the trace event name. The default is NULL.



</dd><dt><b>

 *<include\_audit\_events\>* 

</b></dt>
<dd>

Use this optional BIT parameter to specify whether or not audit events are returned. This parameter can be 0 \(do not return audit events\) or 1 \(return audit events\). By default, audit events are not returned \(0 is the default\).



</dd>
</dl>



<a name="loio8179d2976ce210148418a9a15900e7e2__sp_trace_events_resultset1"/>

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

Returns the name of the trace event. System trace event names have the prefix SYS\_.



</td>
</tr>
<tr>
<td valign="top">

description



</td>
<td valign="top">

LONG VARCHAR



</td>
<td valign="top">

Returns a description of what the trace event captures.



</td>
</tr>
<tr>
<td valign="top">

severity



</td>
<td valign="top">

TINYINT



</td>
<td valign="top">

Returns the severity level of the trace event.



</td>
</tr>
<tr>
<td valign="top">

is\_system



</td>
<td valign="top">

BIT



</td>
<td valign="top">

Returns 1 for system trace events and 0 otherwise.



</td>
</tr>
<tr>
<td valign="top">

is\_temporary



</td>
<td valign="top">

BIT



</td>
<td valign="top">

Returns 1 for temporary trace events and 0 otherwise.



</td>
</tr>
</table>



<a name="loio8179d2976ce210148418a9a15900e7e2__sp_trace_events_remarks1"/>

## Remarks

This procedure returns information about both system-defined and user-defined trace events in the database. It returns the details for the specified trace event or for all trace events if *<event\_name\>* isn’t supplied or is NULL.


<table>
<tr>
<th valign="top">

Level



</th>
<th valign="top">

Severity value range



</th>
</tr>
<tr>
<td valign="top">

ALWAYS



</td>
<td valign="top">

0



</td>
</tr>
<tr>
<td valign="top">

CRITICAL



</td>
<td valign="top">

1–50



</td>
</tr>
<tr>
<td valign="top">

ERROR



</td>
<td valign="top">

51–100



</td>
</tr>
<tr>
<td valign="top">

WARNING



</td>
<td valign="top">

101–150



</td>
</tr>
<tr>
<td valign="top">

INFORMATION



</td>
<td valign="top">

151–200



</td>
</tr>
<tr>
<td valign="top">

DEBUG



</td>
<td valign="top">

201–255



</td>
</tr>
</table>



<a name="loio8179d2976ce210148418a9a15900e7e2__sp_trace_events_priv1"/>

## Privileges



### 

Requires all of the following:

-   EXECUTE object-level privilege on the procedure
-   MANAGE ANY TRACE SESSION system privilege
-   MANAGE AUDITING system privilege



<a name="loio8179d2976ce210148418a9a15900e7e2__sp_trace_events_sideeffect1"/>

## Side Effects

None.



The following statement returns a list of user-defined trace events in the database:

```
SELECT * FROM dbo.sp_trace_events( )
WHERE is_system = 0;
```

**Related Information**  


[sp_trace_events System Procedure for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/9897bebbf9314d72a926d9adae52ead8.html "Returns information about the trace events in the database.") :arrow_upper_right:

