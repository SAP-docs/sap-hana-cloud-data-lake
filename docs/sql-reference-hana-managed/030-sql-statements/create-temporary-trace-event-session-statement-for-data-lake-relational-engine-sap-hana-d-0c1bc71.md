<!-- loio0c1bc711bafd418da40a48480179d22e -->

# CREATE TEMPORARY TRACE EVENT SESSION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Creates a user trace event session.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user. It cannot be run using the REMOTE\_EXECUTE procedure.



```
CREATE [ OR REPLACE ] TEMPORARY TRACE EVENT SESSION <session-name> 
<event-definition> [ ,... ]
[ <target-definition> ]
```

```
<event-definition> :
ADD TRACE EVENT <trace-event-name> [ ( WHERE <search-condition> ) ]
```

```
<target-definition> :
ADD TARGET FILE
  ( SET <target-parameter-name>=<target-parameter-value> [ ,... ] )
```

```
<target-parameter-name> :
{ filename_prefix
 | flush_on_write
 | ["compressed"] }
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio0c1bc711bafd418da40a48480179d22e__section_rz4_s5g_1rb"/>

## Parameters


<dl class="glossary">
<dt><b>

OR REPLACE clause

</b></dt>
<dd>

Specifying CREATE OR REPLACE creates a trace event session or replaces an existing trace event session with the same name.



</dd><dt><b>

WHERE clause

</b></dt>
<dd>

The WHERE clause allows an event to be traced conditionally based on its properties, and can contain expressions that refer to constants and event fields. If there are built-in functions used in *<search-condition\>*, then they are evaluated on the connection generating the event. For example, using `connection_property('number') = 101` logs only events for connections with the number 101.

*<search-condition\>* is applied before events are sent to *<target-definition\>*. If *<search-condition\>* returns FALSE \(or UNKNOWN\), then the event is not sent to the target.

*<search-condition\>* returns an error if it contains any of the following:

-   Sub-queries

-   User-defined functions

-   Sequences

-   Host variables

-   Column references \(may refer to fields of the event but not WHERE clause of the event\)

-   Connection or database variables




</dd><dt><b>

 *<session-name\>* 

</b></dt>
<dd>

The name of the trace event session.



</dd><dt><b>

 *<trace-event-name\>* 

</b></dt>
<dd>

The name of the trace event in the session. System- and user-defined trace events are supported. Call the sp\_trace\_events system procedure to obtain a list of system-defined trace events.



</dd><dt><b>

 *<target-parameter-name\>* 

</b></dt>
<dd>

The following target parameters are supported:


<table>
<tr>
<th valign="top">

 *<target-parameter-name\>* 



</th>
<th valign="top">

 *<target-parameter-value\>* 



</th>
</tr>
<tr>
<td valign="top">

filename\_prefix



</td>
<td valign="top">

\(Required\) An ETD file name prefix with or without a path. ETD files have the extension `.etd`.



</td>
</tr>
<tr>
<td valign="top">

flush\_on\_write



</td>
<td valign="top">

A boolean \(true or false\) value that controls whether disk buffers are flushed for each event that is logged. The default is false. When flushing is enabled, the performance of the database server may be reduced if many trace events are being logged.



</td>
</tr>
<tr>
<td valign="top">

\[compressed\]



</td>
<td valign="top">

A boolean \(true or false\) value that controls compression of the ETD file to conserve disk space. The default is false. Use brackets with this parameter name because it is a keyword in other contexts.



</td>
</tr>
</table>



</dd>
</dl>



<a name="loio0c1bc711bafd418da40a48480179d22e__section_j3q_t5g_1rb"/>

## Remarks

Trace event sessions do not run until they are explicitly started with the ALTER TRACE EVENT SESSION statement. Trace event sessions capture trace events related to system behavior or for a particular user. Trace event sessions are stored in memory and are dropped when the database server stops if they have not been dropped explicitly.



<a name="loio0c1bc711bafd418da40a48480179d22e__section_e53_p2s_wwb"/>

## Privileges



### 

You have the MANAGE ANY TRACE SESSION system privilege.



<a name="loio0c1bc711bafd418da40a48480179d22e__section_sfk_yxw_ysb"/>

## Privileges



### 

You have the MANAGE ANY TRACE SESSION system privilege.



<a name="loio0c1bc711bafd418da40a48480179d22e__section_drm_55g_1rb"/>

## Side Effects

None



<a name="loio0c1bc711bafd418da40a48480179d22e__section_i2j_v5g_1rb"/>

## Standards


<dl>
<dt><b>

ANSI/ISO SQL Standard

</b></dt>
<dd>

Not in the standard.



</dd>
</dl>



The following statement creates an event tracing session that records information about the user-defined event my\_event and the system-defined event SYS\_ConsoleLog\_Information to a file named `my_trace_file`:

```
CREATE TEMPORARY TRACE EVENT SESSION my_session
    ADD TRACE EVENT my_event -- user event
    ADD TRACE EVENT SYS_ConsoleLog_Information -- system event
    ADD TARGET FILE (SET filename_prefix='my_trace_file', [compressed]=1); -- add a target
```

The following statement creates an event tracing session called MySession that records connection events for user HDLADMIN:

```
CREATE TEMPORARY TRACE EVENT SESSION MySession 

ADD TRACE EVENT SYS_RLL_Connect 

( WHERE user='HDLADMIN' );
```

**Related Information**  


[CREATE TEMPORARY TRACE EVENT SESSION Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/816cf4d46ce2101485eddafc5b7ce186.html "Creates a user trace event session.") :arrow_upper_right:

