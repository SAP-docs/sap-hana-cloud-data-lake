<!-- loioa6242a7684f210158944f38f0146ea62 -->

# ROLLBACK TO SAVEPOINT Statement for Data Lake Relational Engine

Cancels any changes made since a savepoint was established. Changes made prior to the savepoint are not undone; they are still pending.



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
ROLLBACK TO SAVEPOINT [ <savepoint-name> ]
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa6242a7684f210158944f38f0146ea62__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

*<savepoint-name\>*

</b></dt>
<dd>

An identifier that was specified on a `SAVEPOINT` statement within the current transaction. If *<savepoint-name\>* is omitted, the most recent savepoint is used. Any savepoints since the named savepoint are automatically released.



</dd>
</dl>



<a name="loioa6242a7684f210158944f38f0146ea62__section_hp2_y2x_ccb"/>

## Remarks

There must have been a corresponding `SAVEPOINT` within the current transaction.



<a name="loioa6242a7684f210158944f38f0146ea62__IQ_Permissions"/>

## Privileges

None



<a name="loioa6242a7684f210158944f38f0146ea62__IQ_Standards"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar.
-   SAP database products – not supported by SAP Adaptive Server Enterprise. To implement similar features in an SAP ASE-compatible manner, you can use nested transactions.

**Related Information**  


[RELEASE SAVEPOINT Statement for Data Lake Relational Engine](release-savepoint-statement-for-data-lake-relational-engine-a622de8.md "Releases a savepoint within the current transaction.")

[ROLLBACK Statement for Data Lake Relational Engine](rollback-statement-for-data-lake-relational-engine-a623fa5.md "Undoes any changes made since the last COMMIT or ROLLBACK.")

[SAVEPOINT Statement for Data Lake Relational Engine](savepoint-statement-for-data-lake-relational-engine-a624878.md "Establishes a savepoint within the current transaction.")

