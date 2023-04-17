<!-- loio3be2e9d86c5f10148a5cdff28ac55004 -->

# Lost Updates

When using an updatable cursor, it is important to guard against lost updates.

A lost update is a scenario in which two or more transactions update the same row, but neither transaction is aware of the modification made by the other transaction, and the second change overwrites the first modification.

The following example illustrates this problem:

1.  An application opens a cursor on the following query against the sample database.

    ```
    SELECT ID, Quantity
    FROM Products;
    ```


    <table>
    <tr>
    <th valign="top">

    ID


    
    </th>
    <th valign="top">

    Quantity


    
    </th>
    </tr>
    <tr>
    <td valign="top">

    300


    
    </td>
    <td valign="top">

    28


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    301


    
    </td>
    <td valign="top">

    54


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    302


    
    </td>
    <td valign="top">

    75


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    ...


    
    </td>
    <td valign="top">

    ...


    
    </td>
    </tr>
    </table>
    
2.  The application fetches the row with ID = 300 through the cursor.

3.  A separate transaction updates the row using the following statement:

    ```
    UPDATE Products
    SET Quantity = Quantity - 10
    WHERE ID = 300;
    ```

4.  The application then updates the row through the cursor to a value of `(Quantity - 5)`.

5.  The correct final value for the row would be 13. If the cursor had prefetched the row, the new value of the row would be 23. The update from the separate transaction is lost.


In a database application, the potential for a lost update exists at any isolation level if changes are made to rows without verification of their values beforehand. At higher isolation levels \(2 and 3\), locking \(read, intent, and write locks\) can be used to ensure that changes to rows cannot be made by another transaction once the row has been read by the application. However, at isolation levels 0 and 1, the potential for lost updates is greater: at isolation level 0, read locks are not acquired to prevent subsequent changes to the data, and isolation level 1 only locks the current row. Lost updates cannot occur when using snapshot isolation since any attempt to change an old value results in an update conflict. Also, the use of prefetching at isolation level 1 can also introduce the potential for lost updates, since the result set row that the application is positioned on, which is in the client's prefetch buffer, may not be the same as the current row that the server is positioned on in the cursor.

To prevent lost updates from occurring with cursors at isolation level 1, the database server supports three different concurrency control mechanisms that can be specified by an application:

1.  The acquisition of intent row locks on each row in the cursor as it is fetched. Intent locks prevent other transactions from acquiring intent or write locks on the same row, preventing simultaneous updates. However, intent locks do not block read row locks, so they do not affect the concurrency of read-only statements.

2.  The use of a value-sensitive cursor. Value-sensitive cursors can be used to track when an underlying row has changed, or has been deleted, so that the application can respond.

3.  The use of FETCH FOR UPDATE, which acquires an intent row lock for that specific row.


How these alternatives are specified depends on the interface used by the application. For the first two alternatives that pertain to a SELECT statement:

-   In ODBC, lost updates cannot occur because the application must specify a cursor concurrency parameter to the SQLSetStmtAttr function when declaring an updatable cursor. This parameter is one of SQL\_CONCUR\_LOCK, SQL\_CONCUR\_VALUES, SQL\_CONCUR\_READ\_ONLY, or SQL\_CONCUR\_TIMESTAMP. For SQL\_CONCUR\_LOCK, the database server acquires row intent locks. For SQL\_CONCUR\_VALUES and SQL\_CONCUR\_TIMESTAMP, a value-sensitive cursor is used. SQL\_CONCUR\_READ\_ONLY is used for read-only cursors, and is the default.

-   In JDBC, the concurrency setting for a statement is similar to that of ODBC. The JDBC driver supports the JDBC concurrency values RESULTSET\_CONCUR\_READ\_ONLY and RESULTSET\_CONCUR\_UPDATABLE. The first value corresponds to the ODBC concurrency setting SQL\_CONCUR\_READ\_ONLY and specifies a read-only statement. The second value corresponds to the ODBC SQL\_CONCUR\_LOCK setting, so row intent locks are used to prevent lost updates. Value-sensitive cursors cannot be specified directly in the JDBC driver.

-   In jConnect, updatable cursors are supported at the API level, but the underlying implementation \(using TDS\) does not support updates through a cursor. Instead, jConnect sends a separate UPDATE statement to the database server to update the specific row. To avoid lost updates, the application must run at isolation level 2 or higher. Alternatively, the application can issue separate UPDATE statements from the cursor, but you must ensure that the UPDATE statement verifies that the row values have not been altered since the row was read by placing appropriate conditions in the UPDATE statement's WHERE clause.

-   In Embedded SQL, a concurrency specification can be set by including syntax within the SELECT statement itself, or in the cursor declaration. In the SELECT statement, the syntax SELECT...FOR UPDATE BY LOCK causes the database server to acquire intent row locks on the result set.

    Alternatively, SELECT...FOR UPDATE BY \[ VALUES | TIMESTAMP \] causes the database server to change the cursor type to a value-sensitive cursor, so that if a specific row has been changed since the row was last read through the cursor, the application receives either a warning \(SQLE\_ROW\_UPDATED\_WARNING\) on a FETCH statement, or an error \(SQLE\_ROW\_UPDATED\_SINCE\_READ\) on an UPDATE WHERE CURRENT OF statement. If the row was deleted, the application also receives an error \(SQLE\_NO\_CURRENT\_ROW\).


FETCH FOR UPDATE functionality is also supported by the Embedded SQL and ODBC interfaces, although the details differ depending on the API that is used.

In Embedded SQL, the application uses FETCH FOR UPDATE, rather than FETCH, to cause an intent lock to be acquired on the row. In ODBC, the application uses the API call SQLSetPos with the operation argument SQL\_POSITION or SQL\_REFRESH, and the lock type argument SQL\_LOCK\_EXCLUSIVE, to acquire an intent lock on a row. These are long-term locks that are held until the transaction is committed or rolled back.

