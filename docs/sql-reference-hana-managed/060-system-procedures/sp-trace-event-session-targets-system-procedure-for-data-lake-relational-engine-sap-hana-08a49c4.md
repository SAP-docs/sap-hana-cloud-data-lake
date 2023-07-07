<!-- loio08a49c4ce49d4d44b534b74d5e9aac35 -->

# sp\_trace\_event\_session\_targets System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Lists the targets of a trace session.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) system procedure can be used when:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user. It cannot be run using the REMOTE\_EXECUTE procedure.



```
sp_trace_event_session_targets(
   [ <session_name>  
   [, <include_server_sessions>
   [, <include_audit_events> ] ] ]
)
```



<a name="loio08a49c4ce49d4d44b534b74d5e9aac35__section_yvv_242_srb"/>

## Parameters


<dl>
<dt><b>

 *<session\_name\>* 

</b></dt>
<dd>

Use this optional CHAR\(256\) parameter to specify the name of the trace event session. The default is NULL. If a session name is not specified or is NULL, information is returned about all trace event sessions in the database.



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



<a name="loio08a49c4ce49d4d44b534b74d5e9aac35__section_n2j_f42_srb"/>

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



<a name="loio08a49c4ce49d4d44b534b74d5e9aac35__section_gjx_f42_srb"/>

## Remarks

A target is the location where the trace event session information is being logged \(such as a file or database server message log\).



## Privileges

Requires one of:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loio08a49c4ce49d4d44b534b74d5e9aac35__section_wc4_g42_srb"/>

## Side Effects

None.



The following statement returns information about all trace event sessions in the database:

```
SELECT * FROM dbo.sp_trace_event_session_targets( );
```

**Related Information**  


[sp_trace_event_session_targets System Procedure for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/8179bf806ce210148693c5362783c940.html "Lists the targets of a trace session.") :arrow_upper_right:

