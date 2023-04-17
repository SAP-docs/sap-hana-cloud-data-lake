<!-- loioe3c01f5594f0442daf8275954bc2bb57 -->

# NOTIFY TRACE EVENT Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Logs a user-defined trace event to a trace session.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user. It cannot be run using the REMOTE\_EXECUTE procedure.



```
NOTIFY TRACE EVENT <trace-event-name> ( [ <param1> [ ,... ] ] )
```



<a name="loioe3c01f5594f0442daf8275954bc2bb57__section_c1f_mmw_brb"/>

## Parameters

  *<trace-event-name\>* 
 :   The trace event name must be the name of a user-defined trace event. It cannot be a system-defined trace event.

   *<param1\>* 
 :   The values of the trace event fields.

 

<a name="loioe3c01f5594f0442daf8275954bc2bb57__section_c51_nmw_brb"/>

## Remarks

This statement is used to notify any sessions that include the specified trace event. If a trace event is not being traced by any session, then this statement has no effect and the parameters are not evaluated \(for example, by a call to a user-defined function\).



<a name="loioe3c01f5594f0442daf8275954bc2bb57__section_f3m_tyw_ysb"/>

## Privileges

You have the NOTIFY TRACE EVENT system privilege.



<a name="loioe3c01f5594f0442daf8275954bc2bb57__section_zpm_pmw_brb"/>

## Side Effects

None



<a name="loioe3c01f5594f0442daf8275954bc2bb57__section_n5v_pmw_brb"/>

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


[NOTIFY TRACE EVENT Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/8171e4fe6ce21014b5a9e34baa895aac.html "Logs a user-defined trace event to a trace session.") :arrow_upper_right:

