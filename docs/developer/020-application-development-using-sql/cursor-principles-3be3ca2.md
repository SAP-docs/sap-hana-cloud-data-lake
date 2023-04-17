<!-- loio3be3ca2f6c5f10148153ae4b2673f7f0 -->

# Cursor Principles

To use a cursor, there are some basic steps to follow.

1.  Prepare and execute a statement.

    Execute a statement using the usual method for the interface. You can prepare and then execute the statement, or you can execute the statement directly.

    With ADO.NET, only the SACommand.ExecuteReader method returns a cursor. It provides a read-only, forward-only cursor.

2.  Test to see if the statement returns a result set.

    A cursor is implicitly opened when a statement that creates a result set is executed. When the cursor is opened, it is positioned before the first row of the result set.

3.  Fetch results.

    Although simple fetch operations move the cursor to the next row in the result set, more complicated movement around the result set is also possible.

4.  Close the cursor.

    When you have finished with the cursor, close it to free associated resources.

5.  Free the statement.

    If you used a prepared statement, free it to reclaim memory.


The approach for using a cursor in Embedded SQL differs from the approach used in other interfaces. Follow these general steps to use a cursor in Embedded SQL:

1.  Prepare a statement.

    Cursors generally use a statement handle rather than a string. Prepare a statement to have a handle available.

2.  Declare the cursor.

    Each cursor refers to a single SELECT or CALL statement. When you declare a cursor, you state the name of the cursor and the statement it refers to.

3.  Open the cursor.

    For a CALL statement, opening the cursor executes the procedure up to the point where the first row is about to be obtained.

4.  Fetch results.

    Although simple fetch operations move the cursor to the next row in the result set, more complicated movement around the result set is also possible. How you declare the cursor determines which fetch operations are available to you.

5.  Close the cursor.

    When you have finished with the cursor, close it. This frees any resources associated with the cursor.

6.  Drop the statement.

    To free the memory associated with the statement, you must drop the statement.


