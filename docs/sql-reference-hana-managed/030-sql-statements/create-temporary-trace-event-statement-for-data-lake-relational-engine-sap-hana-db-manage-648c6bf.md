<!-- loio648c6bf7ab2444cd8182c4a06d3dad86 -->

# CREATE TEMPORARY TRACE EVENT Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Creates a user trace event that persists until the database is stopped.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user. It cannot be run using the REMOTE\_EXECUTE procedure.



```
CREATE [ OR REPLACE ] TEMPORARY TRACE EVENT <trace-event-name> 
[ WITH SEVERITY {
 <0-255>
 | ALWAYS
 | CRITICAL
 | ERROR
 | WARNING
 | INFORMATION
 | DEBUG } ]
[ ( <field-name> <field-type> [ , ... ] ] )
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio648c6bf7ab2444cd8182c4a06d3dad86__section_oxt_vtg_1rb"/>

## Parameters


<dl class="glossary">
<dt><b>

 *<trace-event-name\>* 

</b></dt>
<dd>

Specify a user trace event name. User trace event names cannot start with the prefix SYS\_. System trace event names cannot be specified.



</dd><dt><b>

OR REPLACE clause

</b></dt>
<dd>

Create a new trace event, or replace an existing trace event with the same name.



</dd><dt><b>

WITH SEVERITY clause

</b></dt>
<dd>

If the severity level is not specified, the default severity level \(DEBUG\) is used. User trace events are owned by the database that the user was connected to when the trace event was created. The supported severity values are:


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

1-50



</td>
</tr>
<tr>
<td valign="top">

ERROR



</td>
<td valign="top">

51-100



</td>
</tr>
<tr>
<td valign="top">

WARNING



</td>
<td valign="top">

101-150



</td>
</tr>
<tr>
<td valign="top">

INFORMATION



</td>
<td valign="top">

151-200



</td>
</tr>
<tr>
<td valign="top">

DEBUG



</td>
<td valign="top">

201-255



</td>
</tr>
</table>



</dd><dt><b>

 *<field-name\>* 

</b></dt>
<dd>

The field that gathers information of a specific type from the user trace event. The field must be a valid identifier.



</dd><dt><b>

 *<field-type\>* 

</b></dt>
<dd>

You can use any data type that is supported for a column except an array type.



</dd>
</dl>



<a name="loio648c6bf7ab2444cd8182c4a06d3dad86__section_opw_wtg_1rb"/>

## Remarks

A trace event is stored in memory and is dropped when the database server stops if it hasn’t been dropped explicitly.



<a name="loio648c6bf7ab2444cd8182c4a06d3dad86__section_bry_x2s_wwb"/>

## Privileges

You have the MANAGE ANY TRACE SESSION system privilege.

See [GRANT System Privilege Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a3dfcb0284f21015b74ac3cded42ee69.html "Grants specific system privileges to users or roles, with or without administrative rights.") :arrow_upper_right: for assistance with granting privileges.



<a name="loio648c6bf7ab2444cd8182c4a06d3dad86__section_y24_xtg_1rb"/>

## Side Effects

None



<a name="loio648c6bf7ab2444cd8182c4a06d3dad86__section_oz1_ytg_1rb"/>

## Standards


<dl>
<dt><b>

ANSI/ISO SQL Standard

</b></dt>
<dd>

Not in the standard.



</dd>
</dl>



The following statement creates a user trace event:

```
CREATE TEMPORARY TRACE EVENT my_event( id INTEGER, information LONG VARCHAR );
```

**Related Information**  


[CREATE TEMPORARY TRACE EVENT Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/816cfdb66ce21014b8ff8c954b0293b5.html "Creates a user trace event that persists until the database is stopped.") :arrow_upper_right:

