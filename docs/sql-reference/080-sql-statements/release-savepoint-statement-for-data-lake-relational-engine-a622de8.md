<!-- loioa622de8d84f21015be4fc3e6a28ea41e -->

# RELEASE SAVEPOINT Statement for Data Lake Relational Engine

Releases a savepoint within the current transaction.



<a name="loioa622de8d84f21015be4fc3e6a28ea41e__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
RELEASE SAVEPOINT [ <savepoint-name> ]
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa622de8d84f21015be4fc3e6a28ea41e__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

*<savepoint-name\>*

</b></dt>
<dd>

An identifier specified on a `SAVEPOINT` statement within the current transaction. If *<savepoint-name\>* is omitted, the most recent savepoint is released.



</dd>
</dl>



<a name="loioa622de8d84f21015be4fc3e6a28ea41e__IQ_Usage"/>

## Remarks

Releasing a savepoint does not perform any type of `COMMIT`; it simply removes the savepoint from the list of currently active savepoints.

There must have been a corresponding `SAVEPOINT` within the current transaction.



<a name="loioa622de8d84f21015be4fc3e6a28ea41e__IQ_Permissions"/>

## Privileges

None



<a name="loioa622de8d84f21015be4fc3e6a28ea41e__IQ_Standards"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise. A similar feature is available in an SAP ASE-compatible manner using nested transactions.

**Related Information**  


[ROLLBACK TO SAVEPOINT Statement for Data Lake Relational Engine](rollback-to-savepoint-statement-for-data-lake-relational-engine-a6242a7.md "Cancels any changes made since a savepoint was established. Changes made prior to the savepoint are not undone; they are still pending.")

[SAVEPOINT Statement for Data Lake Relational Engine](savepoint-statement-for-data-lake-relational-engine-a624878.md "Establishes a savepoint within the current transaction.")

