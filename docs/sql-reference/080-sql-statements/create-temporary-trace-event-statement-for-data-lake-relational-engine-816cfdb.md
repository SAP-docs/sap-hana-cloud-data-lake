<!-- loio816cfdb66ce21014b8ff8c954b0293b5 -->

# CREATE TEMPORARY TRACE EVENT Statement for Data Lake Relational Engine

Creates a user trace event that persists until the database is stopped.



<a name="loio816cfdb66ce21014b8ff8c954b0293b5__section_azh_5fj_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



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



<a name="loio816cfdb66ce21014b8ff8c954b0293b5__create_temp_trace_event_parameters1"/>

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



<a name="loio816cfdb66ce21014b8ff8c954b0293b5__create_temp_trace_event_remarks1"/>

## Remarks

A trace event is stored in memory and is dropped when the database server stops if it hasn’t been dropped explicitly.



<a name="loio816cfdb66ce21014b8ff8c954b0293b5__create_temp_trace_event_privileges1"/>

## Privileges

You have the MANAGE ANY TRACE SESSION system privilege.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



<a name="loio816cfdb66ce21014b8ff8c954b0293b5__create_temp_trace_event_side_effects1"/>

## Side Effects

None



<a name="loio816cfdb66ce21014b8ff8c954b0293b5__create_temp_trace_event_standards1"/>

## Standards


<dl>
<dt><b>

ANSI/ISO SQL Standard

</b></dt>
<dd>

Not in the standard.



</dd>
</dl>



## Example

The following statement creates a user trace event:

```
CREATE TEMPORARY TRACE EVENT my_event( id INTEGER, information LONG VARCHAR );
```

**Related Information**  


[DROP TRACE EVENT Statement for Data Lake Relational Engine](drop-trace-event-statement-for-data-lake-relational-engine-816f81a.md "Drops a user-defined trace event.")

[CREATE TEMPORARY TRACE EVENT Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/648c6bf7ab2444cd8182c4a06d3dad86.html "Creates a user trace event that persists until the database is stopped.") :arrow_upper_right:

