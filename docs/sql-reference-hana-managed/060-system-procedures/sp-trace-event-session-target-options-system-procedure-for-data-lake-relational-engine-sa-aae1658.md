<!-- loioaae165896e5d4689b72835021f67795e -->

# sp\_trace\_event\_session\_target\_options System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Lists the target options for a trace event session.



<a name="loioaae165896e5d4689b72835021f67795e__section_aky_kcb_1yb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) system procedure can be used when:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.

> ### Restriction:  
> This syntax cannot be run when connected to SAP HANA database as a SAP HANA database user and using SAP HANA database REMOTE\_EXECUTE or REMOTE\_EXECUTE\_QUERY.



```
sp_trace_event_session_target_options(
   [ <session_name>  
   [, <include_server_sessions>
   [, <include_audit_events> ] ] ]
  )
```



<a name="loioaae165896e5d4689b72835021f67795e__section_ul3_tl2_srb"/>

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



<a name="loioaae165896e5d4689b72835021f67795e__section_uxn_qcb_1yb"/>

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



<a name="loioaae165896e5d4689b72835021f67795e__section_vpn_vl2_srb"/>

## Side Effects

None.



## Examples

The following outputs assume the existence of a trace session named my\_session. To create this session, execute:

```
CREATE OR REPLACE TEMPORARY TRACE EVENT SESSION my_session
   ADD TRACE EVENT my_event, 
   ADD TRACE EVENT SYS_ConsoleLog_Information 
   ADD TARGET FILE (SET filename_prefix='my_trace_file', [compressed]=1);
```

This example shows the target options for the trace session my\_session:

```
CALL sp_trace_event_session_target_options('my_session');
```


<table>
<tr>
<th valign="top">

session\_name

</th>
<th valign="top">

is\_server

</th>
<th valign="top">

target\_type

</th>
<th valign="top">

option\_name

</th>
<th valign="top">

option\_value

</th>
</tr>
<tr>
<td valign="top">

my\_session

</td>
<td valign="top">

0

</td>
<td valign="top">

FILE

</td>
<td valign="top">

filename\_prefix

</td>
<td valign="top">

my\_trace\_file

</td>
</tr>
<tr>
<td valign="top">

my\_session

</td>
<td valign="top">

0

</td>
<td valign="top">

FILE

</td>
<td valign="top">

compressed

</td>
<td valign="top">

1

</td>
</tr>
</table>

**Related Information**  


[sp_trace_event_session_target_options System Procedure for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/8179b61a6ce210148e4db24e40891e7d.html "Lists the target options for a trace event session.") :arrow_upper_right:

