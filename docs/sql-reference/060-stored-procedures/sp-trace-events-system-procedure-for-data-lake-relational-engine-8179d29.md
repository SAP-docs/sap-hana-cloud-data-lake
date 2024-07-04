<!-- loio8179d2976ce210148418a9a15900e7e2 -->

# sp\_trace\_events System Procedure for Data Lake Relational Engine

Returns information about the trace events in the database.



<a name="loio8179d2976ce210148418a9a15900e7e2__section_p4t_vqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



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

-   EXECUTE object-level privilege on this procedure
-   MANAGE ANY TRACE SESSION system privilege
-   MANAGE AUDITING system privilege



<a name="loio8179d2976ce210148418a9a15900e7e2__sp_trace_events_sideeffect1"/>

## Side Effects

None.



<a name="loio8179d2976ce210148418a9a15900e7e2__sp_trace_events_examples1"/>

## Examples

This example returns a list of all trace events:

```
CALL sp_trace_events( );
```


<table>
<tr>
<th valign="top">

event\_name

</th>
<th valign="top">

description

</th>
<th valign="top">

severity

</th>
<th valign="top">

is\_system

</th>
<th valign="top">

is\_temporary

</th>
</tr>
<tr>
<td valign="top">

SYS\_HTTP\_Log

</td>
<td valign="top">

event for current http logging

</td>
<td valign="top">

250

</td>
<td valign="top">

1

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

SYS\_ConsoleLog\_Error

</td>
<td valign="top">

Error Console Log messages

</td>
<td valign="top">

100

</td>
<td valign="top">

1

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

SYS\_ConsoleLog\_Warning

</td>
<td valign="top">

Warning Console Log messages

</td>
<td valign="top">

150

</td>
<td valign="top">

1

</td>
<td valign="top">

0

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

This example returns all trace events with a severity level of 100:

```
SELECT * FROM sp_trace_events( ) WHERE SEVERITY=100;
```


<table>
<tr>
<th valign="top">

event\_name

</th>
<th valign="top">

description

</th>
<th valign="top">

severity

</th>
<th valign="top">

is\_system

</th>
<th valign="top">

is\_temporary

</th>
</tr>
<tr>
<td valign="top">

SYS\_ConsoleLog\_Error

</td>
<td valign="top">

Error Console Log messages

</td>
<td valign="top">

100

</td>
<td valign="top">

1

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

SYS\_RLL\_ConnectionError

</td>
<td valign="top">

Event for Connection Error

</td>
<td valign="top">

100

</td>
<td valign="top">

1

</td>
<td valign="top">

0

</td>
</tr>
</table>

This example returns information on the trace event SYS\_HTTP\_LOG:

```
Call sp_trace_events('SYS_HTTP_LOG');
```


<table>
<tr>
<th valign="top">

event\_name

</th>
<th valign="top">

description

</th>
<th valign="top">

severity

</th>
<th valign="top">

is\_system

</th>
<th valign="top">

is\_temporary

</th>
</tr>
<tr>
<td valign="top">

SYS\_HTTP\_Log

</td>
<td valign="top">

event for current http logging

</td>
<td valign="top">

250

</td>
<td valign="top">

1

</td>
<td valign="top">

0

</td>
</tr>
</table>

**Related Information**  


[sp_trace_events System Procedure for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/9897bebbf9314d72a926d9adae52ead8.html "Returns information about the trace events in the database.") :arrow_upper_right:

[CREATE TEMPORARY TRACE EVENT SESSION Statement for Data Lake Relational Engine](../080-sql-statements/create-temporary-trace-event-session-statement-for-data-lake-relational-engine-816cf4d.md "Creates a user trace event session.")

