<!-- loio816f81ae6ce210149309e843cf27de9d -->

# DROP TRACE EVENT Statement for Data Lake Relational Engine

Drops a user-defined trace event.



<a name="loio816f81ae6ce210149309e843cf27de9d__section_azh_5fj_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
DROP TRACE EVENT [ IF EXISTS ] <trace-event-name>
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio816f81ae6ce210149309e843cf27de9d__drop_tracce_event_privileges1"/>

## Privileges

You have the MANAGE ANY TRACE SESSION system privilege.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



<a name="loio816f81ae6ce210149309e843cf27de9d__drop_trace_event_remarks1"/>

## Remarks

This statement only drops user-defined trace events. If you don’t want an error returned when the DROP TRACE EVENT statement attempts to remove a trace event that doesn’t exist, use the IF EXISTS clause. If one ore more event tracing sessions reference the trace event, then the trace event can’t be dropped until all the referencing trace sessions are dropped.



<a name="loio816f81ae6ce210149309e843cf27de9d__drop_trace_event_side_effects1"/>

## Side Effects

None.



<a name="loio816f81ae6ce210149309e843cf27de9d__drop_trace_event_standards1"/>

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

Drop the trace event named my\_event:

```
DROP TRACE EVENT my_event;
```

**Related Information**  


[CREATE TEMPORARY TRACE EVENT Statement for Data Lake Relational Engine](create-temporary-trace-event-statement-for-data-lake-relational-engine-816cfdb.md "Creates a user trace event that persists until the database is stopped.")

[DROP TRACE EVENT Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/63579584baca4c78a6b2f830a2dfcc36.html "Drops a user-defined trace event.") :arrow_upper_right:

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

