<!-- loio6dca296cf61d46dd9305d0d3f24a690a -->

# DROP EVENT Statement for Data Lake Relational Engine

Removes an event from the database.



<a name="loio6dca296cf61d46dd9305d0d3f24a690a__section_azh_5fj_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
DROP EVENT [ IF EXISTS ] <event-name>;
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio6dca296cf61d46dd9305d0d3f24a690a__IQ_Usage"/>

## Remarks

Use the IF EXISTS clause if you do not want an error returned when the DROP EVENT statement attempts to remove an event that does not exist.

Events are not owned, so do not specify an owner \(an owner specification is ignored\).



<a name="loio6dca296cf61d46dd9305d0d3f24a690a__drop_datatype_privileges1"/>

## Privileges

Requires one of:

-   MANAGE ANY EVENT system privilege
-   DROP ANY OBJECT system privilege

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) or [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md) for assistance with granting privileges.



<a name="loio6dca296cf61d46dd9305d0d3f24a690a__IQ_Side_Effects"/>

## Side Effects

-   Automatic commit. Clears the Data window in dbisql.



<a name="loio6dca296cf61d46dd9305d0d3f24a690a__IQ_Standards"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products – supported by SAP Adaptive Server Enterprise



<a name="loio6dca296cf61d46dd9305d0d3f24a690a__IQ_Examples"/>

## Examples

This example drops the event myevent1 from the database.

```
DROP EVENT myevent1;
```

**Related Information**  


[CREATE EVENT Statement for Data Lake Relational Engine](create-event-statement-for-data-lake-relational-engine-a617091.md "Defines an event and its associated handler for automating predefined actions. Also defines scheduled actions.")

[ALTER EVENT Statement for Data Lake Relational Engine](alter-event-statement-for-data-lake-relational-engine-a61251b.md "Changes the definition of an event or its associated handler for automating predefined actions. Also alters the definition of scheduled actions.")

