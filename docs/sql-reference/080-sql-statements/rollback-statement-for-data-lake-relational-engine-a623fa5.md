<!-- loioa623fa5884f210158bea86181c29b760 -->

# ROLLBACK Statement for Data Lake Relational Engine

Undoes any changes made since the last `COMMIT` or `ROLLBACK`.



<a name="loioa623fa5884f210158bea86181c29b760__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
ROLLBACK [ WORK ];
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa623fa5884f210158bea86181c29b760__IQ_Usage"/>

## Remarks

`ROLLBACK` ends a logical unit of work \(transaction\) and undoes all changes made to the database during this transaction. A transaction is the database work done between `COMMIT` or `ROLLBACK` statements on one database connection.



<a name="loioa623fa5884f210158bea86181c29b760__IQ_Permissions"/>

## Privileges

None



<a name="loioa623fa5884f210158bea86181c29b760__IQ_Side_Effects"/>

## Side Effects

-   Closes all cursors not opened WITH HOLD.
-   Releases locks held by the transaction issuing the `ROLLBACK`.



<a name="loioa623fa5884f210158bea86181c29b760__IQ_Standards"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products – supported by SAP Adaptive Server Enterprise

**Related Information**  


[COMMIT Statement for Data Lake Relational Engine](commit-statement-for-data-lake-relational-engine-a615db7.md "Makes changes to the database permanent, or terminates a user-defined transaction.")

[ROLLBACK TO SAVEPOINT Statement for Data Lake Relational Engine](rollback-to-savepoint-statement-for-data-lake-relational-engine-a6242a7.md "Cancels any changes made since a savepoint was established. Changes made prior to the savepoint are not undone; they are still pending.")

