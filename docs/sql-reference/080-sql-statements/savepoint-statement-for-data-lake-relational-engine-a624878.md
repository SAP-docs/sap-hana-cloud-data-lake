<!-- loioa624878684f21015a431830654903eca -->

# SAVEPOINT Statement for Data Lake Relational Engine

Establishes a savepoint within the current transaction.



<a name="loioa624878684f21015a431830654903eca__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
SAVEPOINT [ <savepoint-name> ];
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa624878684f21015a431830654903eca__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

*<savepoint-name\>*

</b></dt>
<dd>

An identifier that can be used in a `RELEASE SAVEPOINT` or `ROLLBACK TO SAVEPOINT` statement.



</dd>
</dl>



<a name="loioa624878684f21015a431830654903eca__IQ_Usage"/>

## Remarks

All savepoints are automatically released when a transaction ends.

Savepoints that are established while a trigger is executing or while an atomic compound statement is executing are automatically released when the atomic operation ends.



<a name="loioa624878684f21015a431830654903eca__IQ_Permissions"/>

## Privileges

None



<a name="loioa624878684f21015a431830654903eca__IQ_Standards"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise. To implement similar features in an SAP ASE-compatible manner, use nested transactions.

**Related Information**  


[RELEASE SAVEPOINT Statement for Data Lake Relational Engine](release-savepoint-statement-for-data-lake-relational-engine-a622de8.md "Releases a savepoint within the current transaction.")

[ROLLBACK TO SAVEPOINT Statement for Data Lake Relational Engine](rollback-to-savepoint-statement-for-data-lake-relational-engine-a6242a7.md "Cancels any changes made since a savepoint was established. Changes made prior to the savepoint are not undone; they are still pending.")

