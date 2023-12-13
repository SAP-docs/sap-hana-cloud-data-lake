<!-- loioa624594684f210159608f69e6d6d2ed8 -->

# ROLLBACK TRANSACTION Statement \[T-SQL\] for Data Lake Relational Engine

Cancels any changes made since a savepoint was established using `SAVE TRANSACTION`. Changes made prior to the `SAVE TRANSACTION` are not undone; they are still pending.



<a name="loioa624594684f210159608f69e6d6d2ed8__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
ROLLBACK TRANSACTION [ <savepoint-name> ];
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa624594684f210159608f69e6d6d2ed8__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

*<savepoint-name\>*

</b></dt>
<dd>

An identifier that was specified on a `SAVE TRANSACTION` statement within the current transaction. If *<savepoint-name\>* is omitted, all outstanding changes are rolled back. Any savepoints since the named savepoint are automatically released.



</dd>
</dl>



<a name="loioa624594684f210159608f69e6d6d2ed8__section_sfc_52x_ccb"/>

## Remarks

There must be a corresponding `SAVE TRANSACTION` within the current transaction.



<a name="loioa624594684f210159608f69e6d6d2ed8__IQ_Permissions"/>

## Privileges

None



<a name="loioa624594684f210159608f69e6d6d2ed8__IQ_Standards"/>

## Standards

SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa624594684f210159608f69e6d6d2ed8__IQ_Examples"/>

## Examples

The following example returns five rows with values 10, 20, and so on. The effect of the delete, but not the prior inserts or update, is undone by the `ROLLBACK TRANSACTION` statement:

```
BEGIN
     SELECT row_num INTO #tmp
     FROM sa_rowgenerator( 1, 5 ) 
     SAVE TRANSACTION before_delete
     UPDATE #tmp SET row_num=row_num*10
     DELETE FROM #tmp WHERE row_num >= 3
     ROLLBACK TRANSACTION before_delete
     SELECT * FROM #tmp
END;
```

**Related Information**  


[BEGIN TRANSACTION Statement \[T-SQL\] for Data Lake Relational Engine](begin-transaction-statement-t-sql-for-data-lake-relational-engine-a61490f.md "Use this statement to begin a user-defined transaction.")

[SAVE TRANSACTION Statement \[T-SQL\] for Data Lake Relational Engine](save-transaction-statement-t-sql-for-data-lake-relational-engine-a624b80.md "Establishes a savepoint within the current transaction.")

