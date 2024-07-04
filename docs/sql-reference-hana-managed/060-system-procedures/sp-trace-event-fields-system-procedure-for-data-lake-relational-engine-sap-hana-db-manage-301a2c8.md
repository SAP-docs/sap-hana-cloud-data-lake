<!-- loio301a2c803cd847d8a5eec27d96cff484 -->

# sp\_trace\_event\_fields System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns information about the fields of the specified trace event.



<a name="loio301a2c803cd847d8a5eec27d96cff484__section_tzf_1db_1yb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) system procedure can be used when:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.

> ### Restriction:  
> This syntax cannot be run when connected to SAP HANA database as a SAP HANA database user and using SAP HANA database REMOTE\_EXECUTE or REMOTE\_EXECUTE\_QUERY.



```
sp_trace_event_fields( 
   [ <event_name> 
   [, <include_audit_events> ] ]
  )
```



<a name="loio301a2c803cd847d8a5eec27d96cff484__section_xrw_5m2_srb"/>

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



<a name="loio301a2c803cd847d8a5eec27d96cff484__section_vn3_vm2_srb"/>

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



<a name="loio301a2c803cd847d8a5eec27d96cff484__section_xn5_vm2_srb"/>

## Remarks

If *<event\_name\>* is NULL, this procedure returns the fields for all trace events.



<a name="loio301a2c803cd847d8a5eec27d96cff484__section_ygs_gdb_1yb"/>

## Privileges



### 


<dl>
<dt><b>

Connected directly to data lake Relational Engine as a data lake Relational Engine user:

</b></dt>
<dd>

Requires all of the following:

-   EXECUTE object-level privilege on this procedure
-   MANAGE ANY TRACE SESSION system privilege
-   MANAGE AUDITING system privilege



</dd>
</dl>



<a name="loio301a2c803cd847d8a5eec27d96cff484__section_fpn_wm2_srb"/>

## Side Effects

None.



## Examples

This example returns information about the fields for all trace event sessions in the database:

```
CALL sp_trace_event_fields( );
```


<table>
<tr>
<th valign="top">

event\_name

</th>
<th valign="top">

field\_name

</th>
<th valign="top">

field\_id

</th>
<th valign="top">

field\_domain

</th>
<th valign="top">

field\_description

</th>
</tr>
<tr>
<td valign="top">

SYS\_HTTP\_Log

</td>
<td valign="top">

message

</td>
<td valign="top">

1

</td>
<td valign="top">

10

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

SYS\_ConsoleLog\_Error

</td>
<td valign="top">

message

</td>
<td valign="top">

1

</td>
<td valign="top">

10

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

SYS\_ConsoleLog\_Warning

</td>
<td valign="top">

message

</td>
<td valign="top">

1

</td>
<td valign="top">

10

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

SYS\_ConsoleLog\_Information

</td>
<td valign="top">

message

</td>
<td valign="top">

1

</td>
<td valign="top">

10

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

SYS\_Mirroring\_Log

</td>
<td valign="top">

dbname\_or\_arbiter

</td>
<td valign="top">

1

</td>
<td valign="top">

10

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

SYS\_Mirroring\_Log

</td>
<td valign="top">

message

</td>
<td valign="top">

2

</td>
<td valign="top">

10

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

SYS\_RLL\_ReqConnect

</td>
<td valign="top">

conn\_id

</td>
<td valign="top">

1

</td>
<td valign="top">

21

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
</tr>
</table>

This example returns information about the fields for the trace event SYS\_RLL\_ReqStatementDrop:

```
CALL sp_trace_event_fields('SYS_RLL_ReqStatementDrop');
```


<table>
<tr>
<th valign="top">

event\_name

</th>
<th valign="top">

field\_name

</th>
<th valign="top">

field\_id

</th>
<th valign="top">

field\_domain

</th>
<th valign="top">

field\_description

</th>
</tr>
<tr>
<td valign="top">

SYS\_RLL\_ReqStatementDrop

</td>
<td valign="top">

conn\_id

</td>
<td valign="top">

1

</td>
<td valign="top">

21

</td>
<td valign="top">

NULL

</td>
</tr>
<tr>
<td valign="top">

SYS\_RLL\_ReqStatementDrop

</td>
<td valign="top">

stmt\_handle

</td>
<td valign="top">

2

</td>
<td valign="top">

21

</td>
<td valign="top">

NULL

</td>
</tr>
</table>

**Related Information**  


[sp_trace_event_fields System Procedure for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/8179a2a56ce210148a18fd12322fa8f2.html "Returns information about the fields of the specified trace event.") :arrow_upper_right:

