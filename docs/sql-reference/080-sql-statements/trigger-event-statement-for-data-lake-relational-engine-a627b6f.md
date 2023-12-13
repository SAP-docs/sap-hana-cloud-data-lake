<!-- loioa627b6ff84f210158a35beaf09a1f5de -->

# TRIGGER EVENT Statement for Data Lake Relational Engine

Triggers a named event. The event may be defined for event triggers or be a scheduled event.



<a name="loioa627b6ff84f210158a35beaf09a1f5de__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
TRIGGER EVENT <event-name> [ ( <parm> = <value>, ... ) ];
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa627b6ff84f210158a35beaf09a1f5de__trigger_event_remarks1"/>

## Remarks

Actions are tied to particular trigger conditions or schedules by a `CREATE EVENT` statement. You can use `TRIGGER EVENT` to force the event handler to execute, even when the scheduled time or trigger condition has not occurred. `TRIGGER EVENT` does not execute disabled event handlers

When a triggering condition causes an event handler to execute, the database server can provide context information to the event handler using the `event_parameter` function. `TRIGGER EVENT` allows you to explicitly supply these parameters, to simulate a context for the event handler.

When you trigger an event, specify the event name. You can list event names by querying the system table `SYSEVENT`. For example:

```
SELECT event_id, event_name FROM SYS.SYSEVENT;
```



<a name="loioa627b6ff84f210158a35beaf09a1f5de__IQ_Permissions"/>

## Privileges

Requires one of:

-   MANAGE EVENT system privilege to trigger self-owned events.
-   MANAGE ANY EVENT system privilege to trigger any event owned by any user.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.

**Related Information**  


[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[ALTER EVENT Statement for Data Lake Relational Engine](alter-event-statement-for-data-lake-relational-engine-a61251b.md "Changes the definition of an event or its associated handler for automating predefined actions. Also alters the definition of scheduled actions.")

[CREATE EVENT Statement for Data Lake Relational Engine](create-event-statement-for-data-lake-relational-engine-a617091.md "Defines an event and its associated handler for automating predefined actions. Also defines scheduled actions.")

