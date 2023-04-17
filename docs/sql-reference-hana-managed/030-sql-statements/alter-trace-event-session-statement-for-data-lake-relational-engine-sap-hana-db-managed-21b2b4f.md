<!-- loio21b2b4f214224d81920ed9bcaf88d7ee -->

# ALTER TRACE EVENT SESSION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Adds or removes trace events or targets from a session, or starts or stops a trace session.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user. It cannot be run using the REMOTE\_EXECUTE procedure.



```
ALTER TRACE EVENT SESSION <session-name> 
[ ON SERVER ]    
{ ADD TRACE EVENT <trace-event-name> [,...]  
  | DROP TRACE EVENT <trace-event-name> [,...]
  | ADD TARGET FILE [ ( SET <target-parameter-name>=<target-parameter-value> [, ...] ) ]
  | DROP TARGET <FILE> [, ...] ]
  | STATE = { START | STOP }
}
```

```
<target-parameter-name> :
{ filename_prefix
 | flush_on_write
 | compressed }
```



<a name="loio21b2b4f214224d81920ed9bcaf88d7ee__section_hky_zlg_1rb"/>

## Parameters

 ON SERVER clause
 :   Alters a trace event session that is recording trace events from all databases on the database server. If this clause is not specified, then only the trace event session on the current database is altered.

   *<trace-event-name\>* 
 :   The name of the trace event in the session. System- and user-defined trace events are supported. Call the sp\_trace\_events system procedure to obtain a list of system-defined trace events.

  ADD TRACE EVENT
 :   The name of the trace event being added to the session.

  DROP TRACE EVENT
 :   The name of the trace event being removed from the session.

  ADD TARGET FILE
 :   The name of the target being added to the session. Information about the trace events that are part of the session is logged to this target \(file\).

  DROP TARGET FILE
 :   The name of the target being removed from the session.

   *<target-parameter-name\>* 
 :   The following target parameters are supported:


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
    
 

<a name="loio21b2b4f214224d81920ed9bcaf88d7ee__section_djb_bmg_1rb"/>

## Remarks

Adding or dropping trace events or targets from a running trace session causes the session to pause briefly to make the changes and then resume after the changes are made. You do not need to stop a tracing session to add or drop trace events or targets. Adding or removing a trace event from a session that has already started has the side effect that some trace events are missed while a session is temporarily paused.



<a name="loio21b2b4f214224d81920ed9bcaf88d7ee__section_iwd_bfq_wwb"/>

## Privileges

You have the MANAGE ANY TRACE SESSION system privilege.



<a name="loio21b2b4f214224d81920ed9bcaf88d7ee__section_mqv_bmg_1rb"/>

## Side Effects

None



<a name="loio21b2b4f214224d81920ed9bcaf88d7ee__section_kb3_cmg_1rb"/>

## Standards

 ANSI/ISO SQL Standard
 :   Not in the standard.

 

The following example creates a trace event called my\_event, a trace event session called my\_session, and starts the session:

```
CREATE TEMPORARY TRACE EVENT my_event( id INTEGER, information LONG VARCHAR );
CREATE TEMPORARY TRACE EVENT SESSION my_session
    ADD TRACE EVENT my_event, -- user event
    ADD TRACE EVENT SYS_ConsoleLog_Information -- system event
    ADD TARGET FILE ( SET filename_prefix='my_trace_file' ); -- add a target
ALTER TRACE EVENT SESSION my_session
     STATE = START;
```

**Related Information**  


[ALTER TRACE EVENT SESSION Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/8169f4176ce21014b768e5f2b0bf8951.html "Adds or removes trace events or targets from a session, or starts or stops a trace session.") :arrow_upper_right:
