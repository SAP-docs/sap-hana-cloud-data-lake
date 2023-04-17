<!-- loio3bd09b046c5f10149f00d41be546a2eb -->

# Cursor Positioning

When a cursor is opened, it is positioned before the first row. You can move the cursor position to an absolute position from the start or the end of the query results, or to a position relative to the current cursor position.

The specifics of how you change cursor position, and what operations are possible, are governed by the programming interface.

The number of row positions you can fetch in a cursor is governed by the size of an integer. You can fetch rows numbered up to number 2147483646, which is one less than the value that can be held in an integer. When using negative numbers \(rows from the end\) you can fetch down to one more than the largest negative value that can be held in an integer.

You can use special positioned update and delete operations to update or delete the row at the current position of the cursor. If the cursor is positioned before the first row or after the last row, an error is returned indicating that there is no corresponding cursor row.

> ### Note:  
> Inserts and some updates to asensitive cursors can cause problems with cursor positioning. Inserted rows are not put at a predictable position within a cursor unless there is an ORDER BY clause on the SELECT statement. Sometimes the inserted row does not appear at all until the cursor is closed and opened again. This occurs if a work table had to be created to open the cursor.
> 
> The UPDATE statement may cause a row to move in the cursor. This happens if the cursor has an ORDER BY clause that uses an existing index \(a work table is not created\). Using STATIC SCROLL cursors alleviates these problems but requires more memory and processing.

