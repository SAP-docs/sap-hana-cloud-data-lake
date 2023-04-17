<!-- loio8171e4fe6ce21014b5a9e34baa895aac -->

# NOTIFY TRACE EVENT Statement for Data Lake Relational Engine

Logs a user-defined trace event to a trace session.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
NOTIFY TRACE EVENT <trace-event-name> ( [ <param1> [ ,... ] ] )
```



<a name="loio8171e4fe6ce21014b5a9e34baa895aac__notify_trace_event_parameters1"/>

## Parameters

  *<trace-event-name\>* 
 :   The trace event name must be the name of a user-defined trace event. It cannot be a system-defined trace event.

   *<param1\>* 
 :   The values of the trace event fields.

 

<a name="loio8171e4fe6ce21014b5a9e34baa895aac__notify_trace_event_remarks1"/>

## Remarks

This statement is used to notify any sessions that include the specified trace event. If a trace event is not being traced by any session, then this statement has no effect and the parameters are not evaluated \(for example, by a call to a user-defined function\).



<a name="loio8171e4fe6ce21014b5a9e34baa895aac__notify_trace_event_priv1"/>

## Privileges

You have the NOTIFY TRACE EVENT system privilege.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



<a name="loio8171e4fe6ce21014b5a9e34baa895aac__notify_trace_event_side_effects1"/>

## Side Effects

None



<a name="loio8171e4fe6ce21014b5a9e34baa895aac__notify_trace_event_standards1"/>

## Standards

 ANSI/ISO SQL Standard
 :   Not in the standard.

 

The following statements log events to the current \(fictitious\) event trace session, my\_event.

```
NOTIFY TRACE EVENT my_event( 1, 'Hello world' ); -- trigger user-defined trace events
NOTIFY TRACE EVENT my_event( 2, 'Hello world 2' );
NOTIFY TRACE EVENT my_event( 3, 'Hello world 3' );
```

**Related Information**  


[NOTIFY TRACE EVENT Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/e3c01f5594f0442daf8275954bc2bb57.html "Logs a user-defined trace event to a trace session.") :arrow_upper_right:

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

