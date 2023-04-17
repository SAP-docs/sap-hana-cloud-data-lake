<!-- loio3bd634516c5f10149335ebbdce153643 -->

# Cursors Used to Modify Rows

Cursors can do more than just read result sets from a query. You can also modify data in the database while processing a cursor.

These operations are commonly called **positioned** insert, update, and delete operations, or PUT operations if the action is an insert.

Not all query result sets allow positioned updates and deletes. If you perform a query on a non-updatable view, then no changes occur to the underlying tables. Also, if the query involves a join, then you must specify which table you want to delete from, or which columns you want to update, when you perform the operations.

Inserts through a cursor can only be executed if any non-inserted columns in the table allow NULL or have defaults.

If multiple rows are inserted into a value-sensitive \(keyset driven\) cursor, they appear at the end of the cursor result set. The rows appear at the end, even if they do not match the WHERE clause of the query or if an ORDER BY clause would normally have placed them at another location in the result set. This behavior is independent of programming interface. For example, it applies when using the Embedded SQL PUT statement or the ODBC SQLBulkOperations function. The value of an AUTOINCREMENT column for the most recent row inserted can be found by selecting the last row in the cursor. For example, in Embedded SQL the value could be obtained using <code>FETCH ABSOLUTE -1 <i class="varname">&lt;cursor-name&gt;</i></code>. As a result of this behavior, the first multiple-row insert for a value-sensitive cursor may be expensive.

ODBC, JDBC, Embedded SQL, and Open Client permit data manipulation using cursors, but ADO.NET does not. With Open Client, you can delete and update rows, but you can only insert rows on a single-table query.



## Which Table Are Rows Deleted From?

If you attempt a positioned delete through a cursor, the table from which rows are deleted is determined as follows:

1.  If no FROM clause is included in the DELETE statement, the cursor must be on a single table only.

2.  If the cursor is for a joined query \(including using a view containing a join\), then the FROM clause must be used. Only the current row of the specified table is deleted. The other tables involved in the join are not affected.

3.  If a FROM clause is included, and no table owner is specified, the table-spec value is first matched against any correlation names.

4.  If a correlation name exists, the table-spec value is identified with the correlation name.

5.  If a correlation name does not exist, the table-spec value must be unambiguously identifiable as a table name in the cursor.

6.  If a FROM clause is included, and a table owner is specified, the table-spec value must be unambiguously identifiable as a table name in the cursor.

7.  The positioned DELETE statement can be used on a cursor open on a view as long as the view is updatable.


