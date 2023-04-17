<!-- loioaae165896e5d4689b72835021f67795e -->

# sp\_trace\_event\_session\_target\_options System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Lists the target options for a trace event session.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) system procedure can be used when:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user. It cannot be run using the REMOTE\_EXECUTE procedure.



```
sp_trace_event_session_target_options(
   [ <session_name>  
   [, <include_server_sessions>
   [, <include_audit_events> ] ] ]
  )
```



<a name="loioaae165896e5d4689b72835021f67795e__section_ul3_tl2_srb"/>

## Parameters

  *<session\_name\>* 
 :   Use this optional CHAR\(256\) parameter to specify the name of the trace event session. The default is NULL. If a session name is not specified or is NULL, information is returned for all trace event sessions.

   *<include\_server\_sessions\>* 
 :   Use this optional BIT parameter to specify whether or not engine-level trace event sessions are returned. This parameter can be 0 \(do not return engine-level trace event sessions\) or 1 \(return engine-level trace event sessions\). The default is 0.

   *<include\_audit\_events\>* 
 :   Use this optional BIT parameter to specify whether or not audit events are returned. This parameter can be 0 \(do not return audit events\) or 1 \(return audit events\). The default is 0.

 

<a name="loioaae165896e5d4689b72835021f67795e__section_inz_tl2_srb"/>

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



<a name="loioaae165896e5d4689b72835021f67795e__section_dyn_5l2_srb"/>

## Remarks

This procedure returns option information for one, or all, trace event sessions for the current database.



## Privileges

You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loioaae165896e5d4689b72835021f67795e__section_vpn_vl2_srb"/>

## Side Effects

None.



The following statement returns information about target options for all trace event sessions in the database:

```
SELECT * FROM dbo.sp_trace_event_session_target_options( );
```

**Related Information**  


[sp_trace_event_session_target_options System Procedure for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/8179b61a6ce210148e4db24e40891e7d.html "Lists the target options for a trace event session.") :arrow_upper_right:

