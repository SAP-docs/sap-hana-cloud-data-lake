<!-- loioa624b80484f210159389bf077847f59d -->

# SAVE TRANSACTION Statement \[T-SQL\] for Data Lake Relational Engine

Establishes a savepoint within the current transaction.



<a name="loioa624b80484f210159389bf077847f59d__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
SAVE TRANSACTION [ <savepoint-name> ];
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa624b80484f210159389bf077847f59d__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

*<savepoint-name\>*

</b></dt>
<dd>

An identifier that can be used in a `ROLLBACK TRANSACTION` statement. All savepoints are automatically released when a transaction ends.



</dd>
</dl>



<a name="loioa624b80484f210159389bf077847f59d__IQ_Permissions"/>

## Privileges

None



<a name="loioa624b80484f210159389bf077847f59d__IQ_Standards"/>

## Standards

SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa624b80484f210159389bf077847f59d__IQ_Examples"/>

## Examples

The following example returns five rows with values 10, 20, and so on. The effect of the delete, but not the prior inserts or update, is undone by the `ROLLBACK TRANSACTION` statement:

```
BEGIN
     SELECT row_num INTO #tmp 
     FROM sa_rowgenerator( 1, 5 ) 
     UPDATE #tmp SET row_num=row_num*10
     SAVE TRANSACTION before_delete
     DELETE FROM #tmp WHERE row_num >= 3
     ROLLBACK TRANSACTION before_delete
     SELECT * FROM #tmp
END;
```

**Related Information**  


[BEGIN TRANSACTION Statement \[T-SQL\] for Data Lake Relational Engine](begin-transaction-statement-t-sql-for-data-lake-relational-engine-a61490f.md "Use this statement to begin a user-defined transaction.")

[ROLLBACK TRANSACTION Statement \[T-SQL\] for Data Lake Relational Engine](rollback-transaction-statement-t-sql-for-data-lake-relational-engine-a624594.md "Cancels any changes made since a savepoint was established using SAVE TRANSACTION. Changes made prior to the SAVE TRANSACTION are not undone; they are still pending.")

