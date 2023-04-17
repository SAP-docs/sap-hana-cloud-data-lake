<!-- loio3bd024bd6c5f1014a3a6e095c8ffc038 -->

# ODBC Cursor Characteristics

ODBC functions that execute statements and manipulate result sets, use cursors to perform their tasks. Applications open a cursor implicitly whenever they execute a SQLExecute or SQLExecDirect function.

For applications that move through a result set only in a forward direction and do not update the result set, cursor behavior is relatively straightforward. By default, ODBC applications request this behavior. ODBC defines a read-only, forward-only cursor, and the database server provides a cursor optimized for performance in this case.

For applications that scroll both forward and backward through a result set, such as many graphical user interface applications, cursor behavior is more complex. ODBC defines a variety of **scrollable cursors** to allow you to build in the behavior that suits your application. The database server provides a full set of cursors to match the ODBC scrollable cursor types.

You set the required ODBC cursor characteristics by calling the SQLSetStmtAttr function that defines statement attributes. You must call SQLSetStmtAttr before executing a statement that creates a result set.

You can use SQLSetStmtAttr to set many cursor characteristics. The characteristics that determine the cursor type that the database server supplies include the following:

SQL\_ATTR\_CURSOR\_SCROLLABLE
:   Set to SQL\_SCROLLABLE for a scrollable cursor and SQL\_NONSCROLLABLE for a forward-only cursor. SQL\_NONSCROLLABLE is the default.

SQL\_ATTR\_CONCURRENCY
:   Set to one of the following values:

    SQL\_CONCUR\_READ\_ONLY
    :   Disallow updates. SQL\_CONCUR\_READ\_ONLY is the default.

    SQL\_CONCUR\_LOCK
    :   Use the lowest level of locking sufficient to ensure that the row can be updated.

    SQL\_CONCUR\_ROWVER
    :   Use optimistic concurrency control, employing a keyset-driven cursor to enable the application to be informed when rows have been modified or deleted as the result set is scrolled.

    SQL\_CONCUR\_VALUES
    :   Use optimistic concurrency control, employing a keyset-driven cursor to enable the application to be informed when rows have been modified or deleted as the result set is scrolled.



The following fragment requests a read-only, scrollable cursor:

```
SQLAllocHandle( SQL_HANDLE_STMT, dbc, &stmt );
SQLSetStmtAttr( stmt, SQL_ATTR_CURSOR_SCROLLABLE,
      SQL_SCROLLABLE, SQL_IS_UINTEGER );
```

