<!-- loio816f77f16ce21014902f832b346099c2 -->

# DROP TRACE EVENT SESSION Statement for Data Lake Relational Engine

Drops a trace event session.



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
DROP TRACE EVENT SESSION [ IF EXISTS ] <session-name> UNCONDITIONALLY [ ON SERVER ]
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio816f77f16ce21014902f832b346099c2__drop_trace_event_session_priv1"/>

## Privileges

You have the MANAGE ANY TRACE SESSION system privilege.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



<a name="loio816f77f16ce21014902f832b346099c2__drop_trace_event_session_remarks1"/>

## Remarks

When UNCONDITIONALLY is specified, dropping an active session automatically stops the session before removing its definition. Otherwise, an error is returned.

Specify the ON SERVER clause to drop a trace event session that is recording trace events from all databases on the database server. If this clause is not specified, then the trace event session on the current database is deleted.



<a name="loio816f77f16ce21014902f832b346099c2__drop_trace_event_session_side_effects1"/>

## Side Effects

None.



<a name="loio816f77f16ce21014902f832b346099c2__drop_trace_event_session_standards1"/>

## Standards


<dl>
<dt><b>

ANSI/ISO SQL Standard

</b></dt>
<dd>

Not in the standard.



</dd>
</dl>



The following statement drops the trace event session named my\_session:

```
DROP TRACE EVENT SESSION my_session;
```

**Related Information**  


[CREATE TEMPORARY TRACE EVENT SESSION Statement for Data Lake Relational Engine](create-temporary-trace-event-session-statement-for-data-lake-relational-engine-816cf4d.md "Creates a user trace event session.")

[DROP TRACE EVENT SESSION Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/1b596abba6ea4afeb9284194d73b4dd2.html "Drops a trace event session.") :arrow_upper_right:

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

