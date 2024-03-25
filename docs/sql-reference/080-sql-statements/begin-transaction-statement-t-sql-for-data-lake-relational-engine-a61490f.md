<!-- loioa61490f284f21015aa60a82fc60f9e76 -->

# BEGIN TRANSACTION Statement \[T-SQL\] for Data Lake Relational Engine

Use this statement to begin a user-defined transaction.



<a name="loioa61490f284f21015aa60a82fc60f9e76__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



## Syntax

```
BEGIN TRAN[SACTION] [ <transaction-name> ]
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa61490f284f21015aa60a82fc60f9e76__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

*<transaction-name\>*

</b></dt>
<dd>

\(Optional\) The name assigned to this transaction. It must be a valid identifier. Use transaction names only on the outermost pair of nested BEGIN/COMMIT or BEGIN/ROLLBACK statements.



</dd>
</dl>



<a name="loioa61490f284f21015aa60a82fc60f9e76__IQ_Usage"/>

## Remarks

> ### Note:  
> BEGIN TRANSACTION is a T-SQL construct and must contain only valid T-SQL commands. You cannot mix T-SQL and non-T-SQL commands.

When executed inside a transaction, the BEGIN TRANSACTION statement increases the nesting level of transactions by one. The nesting level is decreased by a COMMIT statement. When transactions are nested, only the outermost COMMIT makes the changes to the database permanent.

You can control the mode by setting the chained database option. The default setting for ODBC and embedded SQL connections in data lake Relational Engine is On, in which case SAP ASE runs in chained mode. \(ODBC users should also check the AutoCommit ODBC setting\). The default for TDS connections is Off.

In unchained mode, a transaction is implicitly started before any data retrieval or modification statement. These statements include: DELETE, INSERT, OPEN, FETCH, SELECT, and UPDATE. You must still explicitly end the transaction with a COMMIT or ROLLBACK statement.

You cannot alter the chained option within a transaction.

> ### Note:  
> When calling a stored procedure, you should ensure that it operates correctly under the required transaction mode.

The current nesting level is held in the global variable @@trancount. The @@trancount variable has a value of zero before the first BEGIN TRANSACTION statement is executed, and only a COMMIT executed when @@trancount is equal to one makes changes to the database permanent.

A ROLLBACK statement without a transaction or savepoint name always rolls back statements to the outermost BEGIN TRANSACTION \(explicit or implicit\) statement, and cancels the entire transaction.



<a name="loioa61490f284f21015aa60a82fc60f9e76__IQ_Permissions"/>

## Privileges

None



<a name="loioa61490f284f21015aa60a82fc60f9e76__IQ_Standards"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar

**Related Information**  


[COMMIT Statement for Data Lake Relational Engine](commit-statement-for-data-lake-relational-engine-a615db7.md "Makes changes to the database permanent, or terminates a user-defined transaction.")

[ROLLBACK Statement for Data Lake Relational Engine](rollback-statement-for-data-lake-relational-engine-a623fa5.md "Undoes any changes made since the last COMMIT or ROLLBACK.")

[SAVE TRANSACTION Statement \[T-SQL\] for Data Lake Relational Engine](save-transaction-statement-t-sql-for-data-lake-relational-engine-a624b80.md "Establishes a savepoint within the current transaction.")

[ISOLATION\_LEVEL Option for Data Lake Relational Engine](../090-database-options/isolation-level-option-for-data-lake-relational-engine-a63ac6b.md "Controls the locking isolation level for catalog store tables.")

