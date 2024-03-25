<!-- loioa6233dc184f21015a615f14fe71ace91 -->

# RESIGNAL Statement for Data Lake Relational Engine

Resignals an exception condition.



<a name="loioa6233dc184f21015a615f14fe71ace91__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
RESIGNAL [ <exception-name> ]
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa6233dc184f21015a615f14fe71ace91__IQ_Usage"/>

## Remarks

Within an exception handler, `RESIGNAL` lets you quit the compound statement with the exception still active, or quit reporting another named exception. The exception is handled by another exception handler or returned to the application. Any actions by the exception handler before the `RESIGNAL` are undone.



<a name="loioa6233dc184f21015a615f14fe71ace91__IQ_Permissions"/>

## Privileges

None



<a name="loioa6233dc184f21015a615f14fe71ace91__IQ_Standards"/>

## Standards

-   SQL – ISO/ANSI SQL compliant.
-   SAP database products – not supported by SAP Adaptive Server Enterprise. Error handling in Transact-SQL procedures is carried out using the `RAISERROR` statement.



<a name="loioa6233dc184f21015a615f14fe71ace91__IQ_Examples"/>

## Examples

This code fragment returns all exceptions except for “Column Not Found” to the application:

```
...
DECLARE COLUMN_NOT_FOUND EXCEPTION 
	FOR SQLSTATE '52003';
...
EXCEPTION
WHEN COLUMN_NOT_FOUND THEN
SET message='Column not found' ;
WHEN OTHERS THEN
RESIGNAL ;
```

**Related Information**  


[BEGIN … END Statement for Data Lake Relational Engine](begin-end-statement-for-data-lake-relational-engine-a6142de.md "Groups SQL statements together.")

[SIGNAL Statement for Data Lake Relational Engine](signal-statement-for-data-lake-relational-engine-a6266b2.md "Lets you raise an exception condition.")

