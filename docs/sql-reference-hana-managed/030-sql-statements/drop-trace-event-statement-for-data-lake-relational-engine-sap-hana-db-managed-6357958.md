<!-- loio63579584baca4c78a6b2f830a2dfcc36 -->

# DROP TRACE EVENT Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Drops a user-defined trace event.



<a name="loio63579584baca4c78a6b2f830a2dfcc36__section_iyl_lhw_ysb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:

-   Connected directly to data lake Relational Engine **coordinator** as a data lake Relational Engine user. This syntax cannot be run using the REMOTE\_EXECUTE procedure.



```
DROP TRACE EVENT [ IF EXISTS ] <trace-event-name>;
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio63579584baca4c78a6b2f830a2dfcc36__section_scn_mgy_wwb"/>

## Privileges

You have the MANAGE ANY TRACE SESSION system privilege.



<a name="loio63579584baca4c78a6b2f830a2dfcc36__section_p1c_fcr_brb"/>

## Remarks

This statement only drops user-defined trace events. If you don’t want an error returned when the DROP TRACE EVENT statement attempts to remove a trace event that doesn’t exist, use the IF EXISTS clause. If one ore more event tracing sessions reference the trace event, then the trace event can’t be dropped until all the referencing trace sessions are dropped.



<a name="loio63579584baca4c78a6b2f830a2dfcc36__section_zfz_fcr_brb"/>

## Side Effects

None.



<a name="loio63579584baca4c78a6b2f830a2dfcc36__section_fy1_hcr_brb"/>

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


[CREATE TEMPORARY TRACE EVENT Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](create-temporary-trace-event-statement-for-data-lake-relational-engine-sap-hana-db-manage-648c6bf.md "Creates a user trace event that persists until the database is stopped.")

[DROP TRACE EVENT Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/816f81ae6ce210149309e843cf27de9d.html "Drops a user-defined trace event.") :arrow_upper_right:

