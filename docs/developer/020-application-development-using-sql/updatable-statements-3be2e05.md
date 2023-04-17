<!-- loio3be2e0566c5f10148827ccf3837b5293 -->

# Updatable Statements

Clauses in the SELECT statement can affect updatable statements and cursors in various ways.



## Updatability of Read-Only Statements

Specifying FOR READ ONLY in the cursor declaration, or including a FOR READ ONLY clause in the statement, renders the statement read-only. In other words, a FOR READ ONLY clause, or the appropriate read-only cursor declaration when using a client API, overrides any other updatability specification.

If the outermost block of a SELECT statement contains an ORDER BY clause, and the statement does not specify FOR UPDATE, then the cursor is read-only. If the SQL SELECT statement specifies FOR XML, then the cursor is read-only. Otherwise, the cursor is updatable.



## Updatable Statements and Concurrency Control

For updatable statements, both optimistic and pessimistic concurrency control mechanisms on cursors are provided to ensure that a result set stays consistent during scrolling operations. These mechanisms are alternatives to using INSENSITIVE cursors or snapshot isolation, although they have different semantics and tradeoffs.

The specification of FOR UPDATE can affect whether a cursor is updatable. However, the FOR UPDATE syntax has no other effect on concurrency control. If FOR UPDATE is specified with additional parameters, the processing of the statement is altered to incorporate one of two concurrency control options as follows:

Pessimistic
:   For all rows fetched in the cursor's result set, the database server acquires intent row locks to prevent the rows from being updated by any other transaction.

Optimistic
:   The cursor type used by the database server is changed to a keyset-driven cursor \(insensitive row membership, value-sensitive\) so that the application can be informed when a row in the result has been modified or deleted by this, or any other transaction.

Pessimistic or optimistic concurrency is specified at the cursor level either through options with DECLARE CURSOR or FOR statements, or though the concurrency setting API for a specific programming interface. If a statement is updatable and the cursor does not specify a concurrency control mechanism, the statement's specification is used. The syntax is as follows:

FOR UPDATE BY LOCK
:   The database server acquires intent row locks on fetched rows of the result set. These are long-term locks that are held until transaction COMMIT or ROLLBACK.

FOR UPDATE BY \{ VALUES | TIMESTAMP \}
:   The database server uses a keyset-driven cursor to enable the application to be informed when rows have been modified or deleted as the result set is scrolled.



## Restricting Updatable Statements

FOR UPDATE \( *<column-list\>* \) enforces the restriction that only named result set attributes can be modified in a subsequent UPDATE WHERE CURRENT OF statement.

