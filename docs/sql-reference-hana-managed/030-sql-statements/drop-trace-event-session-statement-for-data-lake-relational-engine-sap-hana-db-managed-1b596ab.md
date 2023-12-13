<!-- loio1b596abba6ea4afeb9284194d73b4dd2 -->

# DROP TRACE EVENT SESSION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Drops a trace event session.



<a name="loio1b596abba6ea4afeb9284194d73b4dd2__section_xy5_jhw_ysb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:

-   Connected directly to data lake Relational Engine **coordinator** as a data lake Relational Engine user. This syntax cannot be run using the REMOTE\_EXECUTE procedure.



```
DROP TRACE EVENT SESSION [ IF EXISTS ] <session-name> UNCONDITIONALLY [ ON SERVER ];
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio1b596abba6ea4afeb9284194d73b4dd2__section_xhk_4xw_ysb"/>

## Privileges

You have the MANAGE ANY TRACE SESSION system privilege.



<a name="loio1b596abba6ea4afeb9284194d73b4dd2__section_ulm_s2r_brb"/>

## Remarks

When UNCONDITIONALLY is specified, dropping an active session automatically stops the session before removing its definition. Otherwise, an error is returned.

Specify the ON SERVER clause to drop a trace event session that is recording trace events from all databases on the database server. If this clause is not specified, then the trace event session on the current database is deleted.



<a name="loio1b596abba6ea4afeb9284194d73b4dd2__section_uf4_t2r_brb"/>

## Side Effects

None.



<a name="loio1b596abba6ea4afeb9284194d73b4dd2__section_drg_w2r_brb"/>

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

The following statement drops the trace event session named my\_session:

```
DROP TRACE EVENT SESSION my_session;
```

**Related Information**  


[CREATE TEMPORARY TRACE EVENT SESSION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](create-temporary-trace-event-session-statement-for-data-lake-relational-engine-sap-hana-d-0c1bc71.md "Creates a user trace event session.")

[ALTER TRACE EVENT SESSION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](alter-trace-event-session-statement-for-data-lake-relational-engine-sap-hana-db-managed-21b2b4f.md "Adds or removes trace events or targets from a session, or starts or stops a trace session.")

[DROP TRACE EVENT SESSION Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/816f77f16ce21014902f832b346099c2.html "Drops a trace event session.") :arrow_upper_right:

