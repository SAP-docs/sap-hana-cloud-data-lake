<!-- loioe3c01f5594f0442daf8275954bc2bb57 -->

# NOTIFY TRACE EVENT Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Logs a user-defined trace event to a trace session.



## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:

-   Connected directly to data lake Relational Engine **coordinator** as a data lake Relational Engine user. This syntax cannot be run using the REMOTE\_EXECUTE procedure.



```
NOTIFY TRACE EVENT <trace-event-name> ( [ <param1> [ ,... ] ] );
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioe3c01f5594f0442daf8275954bc2bb57__section_c1f_mmw_brb"/>

## Parameters


<dl class="glossary">
<dt><b>

*<trace-event-name\>* 

</b></dt>
<dd>

The trace event name must be the name of a user-defined trace event. It cannot be a system-defined trace event.



</dd><dt><b>

*<param1\>* 

</b></dt>
<dd>

The values of the trace event fields.



</dd>
</dl>



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


<dl>
<dt><b>

ANSI/ISO SQL Standard

</b></dt>
<dd>

Not in the standard.



</dd>
</dl>



## Example

The following statements log events to the current \(fictitious\) event trace session, my\_event.

```
NOTIFY TRACE EVENT my_event( 1, 'Hello world' ); -- trigger user-defined trace events
NOTIFY TRACE EVENT my_event( 2, 'Hello world 2' );
NOTIFY TRACE EVENT my_event( 3, 'Hello world 3' );
```

**Related Information**  


[NOTIFY TRACE EVENT Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/8171e4fe6ce21014b5a9e34baa895aac.html "Logs a user-defined trace event to a trace session.") :arrow_upper_right:

