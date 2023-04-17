<!-- loio3bd97e086c5f1014b04d9afeb511d8e7 -->

# Row Updates and Deletes Through a Cursor

You can update and delete rows through a cursor.

When you use positioned update statements, you must use the FOR UPDATE clause to indicate that a cursor is updatable using positioned operations.

Cursors are automatically updatable as long as the following conditions are met:

-   The underlying query supports updates.

    That is to say, as long as a data manipulation statement on the columns in the result is meaningful, then positioned data manipulation statements can be carried out on the cursor.

    The ansi\_update\_constraints database option limits the type of queries that are updatable.

-   The cursor type supports updates.

    If you are using a read-only cursor, you cannot update the result set.


ODBC provides two alternatives for carrying out positioned updates and deletes:

-   Use the SQLSetPos function.

    Depending on the parameters supplied \(SQL\_POSITION, SQL\_REFRESH, SQL\_UPDATE, SQL\_DELETE\) SQLSetPos sets the cursor position and allows an application to refresh data, or update, or delete data in the result set.

    This is the method to use with the database server.

-   Send positioned UPDATE and DELETE statements using SQLExecute. This method should not be used with the database server.


