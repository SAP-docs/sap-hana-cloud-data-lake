<!-- loio9897bebbf9314d72a926d9adae52ead8 -->

# sp\_trace\_events System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns information about the trace events in the database.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) system procedure can be used when:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user. It cannot be run using the REMOTE\_EXECUTE procedure.



```
sp_trace_events(
   [ <event_name> 
   [, <include_audit_events> ] ]
)
```



<a name="loio9897bebbf9314d72a926d9adae52ead8__section_ppr_pk2_srb"/>

## Parameters

  *<event\_name\>* 
 :   Use this optional CHAR\(256\) parameter to specify the trace event name. The default is NULL.

   *<include\_audit\_events\>* 
 :   Use this optional BIT parameter to specify whether or not audit events are returned. This parameter can be 0 \(do not return audit events\) or 1 \(return audit events\). By default, audit events are not returned \(0 is the default\).

 

<a name="loio9897bebbf9314d72a926d9adae52ead8__section_d4h_qk2_srb"/>

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



<a name="loio9897bebbf9314d72a926d9adae52ead8__section_tsx_qk2_srb"/>

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



## Privileges

You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loio9897bebbf9314d72a926d9adae52ead8__section_rmr_rk2_srb"/>

## Side Effects

None.



The following statement returns a list of user-defined trace events in the database:

```
SELECT * FROM dbo.sp_trace_events( )
WHERE is_system = 0;
```

**Related Information**  


[sp_trace_event_sessions System Procedure for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/8179c9326ce210149a84c8b4621ed3d9.html "Returns a list of the trace event sessions that are defined for the database.") :arrow_upper_right:

