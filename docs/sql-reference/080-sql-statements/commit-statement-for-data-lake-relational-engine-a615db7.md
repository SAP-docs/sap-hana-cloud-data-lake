<!-- loioa615db7b84f21015b755e11e289ef47c -->

# COMMIT Statement for Data Lake Relational Engine

Makes changes to the database permanent, or terminates a user-defined transaction.



<a name="loioa615db7b84f21015b755e11e289ef47c__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.




<dl>
<dt><b>

Syntax 1 – Ends a Transaction and Makes All Changes Permanent

</b></dt>
<dd>

```
COMMIT [ WORK ];
```



</dd><dt><b>

Syntax 2 – Constructs Nested Transactions

</b></dt>
<dd>

```
COMMIT TRAN[SACTION ] [ <transaction-name> ];
```



</dd>
</dl>



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa615db7b84f21015b755e11e289ef47c__IQ_Usage"/>

## Remarks



### Syntax 1

Data definition statements carry out commits automatically. For information, see the *Side Effects* listing for each SQL statement.

`COMMIT` fails if the database server detects any invalid foreign keys. This makes it impossible to end a transaction with any invalid foreign keys. Usually, foreign key integrity is checked on each data manipulation operation. However, if the database option `WAIT_FOR_COMMIT` is set ON or a particular foreign key was defined with a CHECK ON COMMIT clause, the database server delays integrity checking until the `COMMIT` statement is executed.



### Syntax 2

Nested transactions are similar to savepoints. When executed as the outermost of a set of nested transactions, the statement makes changes to the database permanent. When executed inside a transaction, `COMMIT TRANSACTION` decreases the nesting level of transactions by one. When transactions are nested, only the outermost `COMMIT` makes the changes to the database permanent.

The optional parameter *<transaction-name\>* is the name assigned to this transaction. It must be a valid identifier. Use transaction names only on the outermost pair of nested `BEGIN/COMMIT` or `BEGIN/ROLLBACK` statements.

You can use a set of options to control the detailed behavior of the `COMMIT` statement. See *COOPERATIVE\_COMMIT\_TIMEOUT Option*, *COOPERATIVE\_COMMITS Option*, *DELAYED\_COMMITS Option*, and *DELAYED\_COMMIT\_TIMEOUT Option*. You can use the Commit connection property to return the number of commits on the current connection.

Must be connected to the database.



<a name="loioa615db7b84f21015b755e11e289ef47c__IQ_Permissions"/>

## Privileges

None



<a name="loioa615db7b84f21015b755e11e289ef47c__IQ_Side_Effects"/>

## Side Effects

-   Closes all cursors except those opened WITH HOLD.
-   Deletes all rows of declared temporary tables on this connection, unless they were declared using ON COMMIT PRESERVE ROWS.



<a name="loioa615db7b84f21015b755e11e289ef47c__IQ_Standards"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products – supported by SAP Adaptive Server Enterprise. Syntax 2 is a Transact-SQL extension to ISO/ANSI SQL grammar.



<a name="loioa615db7b84f21015b755e11e289ef47c__IQ_Examples"/>

## Examples

-   The following example commits the current transaction:

    ```
    COMMIT;
    ```

-   The following example shows how the Transact-SQL batch reports successive values of `@@trancount` as 0, 1, 2, 1, 0:

    ```
    PRINT @@trancount
    BEGIN TRANSACTION
    PRINT @@trancount
    BEGIN TRANSACTION
    PRINT @@trancount
    COMMIT TRANSACTION
    PRINT @@trancount
    COMMIT TRANSACTION
    PRINT @@trancount
    go
    ```


**Related Information**  


[BEGIN TRANSACTION Statement \[T-SQL\] for Data Lake Relational Engine](begin-transaction-statement-t-sql-for-data-lake-relational-engine-a61490f.md "Use this statement to begin a user-defined transaction.")

[CONNECT Statement \[ESQL\] \[Interactive SQL\] for Data Lake Relational Engine](connect-statement-esql-interactive-sql-for-data-lake-relational-engine-a6164a2.md "Establishes a connection to the database identified by database-name running on the server identified by engine-name.")

[DISCONNECT Statement \[Interactive SQL\] for Data Lake Relational Engine](disconnect-statement-interactive-sql-for-data-lake-relational-engine-a61bf2a.md "Drops a connection with the database.")

[ROLLBACK Statement for Data Lake Relational Engine](rollback-statement-for-data-lake-relational-engine-a623fa5.md "Undoes any changes made since the last COMMIT or ROLLBACK.")

[SET CONNECTION Statement \[ESQL\] \[Interactive SQL\] for Data Lake Relational Engine](set-connection-statement-esql-interactive-sql-for-data-lake-relational-engine-a6257ba.md "Changes the active database connection.")

[COOPERATIVE\_COMMIT\_TIMEOUT Option for Data Lake Relational Engine](../090-database-options/cooperative-commit-timeout-option-for-data-lake-relational-engine-a631963.md "Governs when a COMMIT entry in the transaction log is written to disk.")

[COOPERATIVE\_COMMITS Option for Data Lake Relational Engine](../090-database-options/cooperative-commits-option-for-data-lake-relational-engine-a631c5c.md "Controls when commits are written to disk.")

[DELAYED\_COMMITS Option for Data Lake Relational Engine](../090-database-options/delayed-commits-option-for-data-lake-relational-engine-a634f55.md "Determines when the server returns control to an application following a COMMIT.")

[DELAYED\_COMMIT\_TIMEOUT Option for Data Lake Relational Engine](../090-database-options/delayed-commit-timeout-option-for-data-lake-relational-engine-a634c64.md "Determines when the server returns control to an application following a COMMIT.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

