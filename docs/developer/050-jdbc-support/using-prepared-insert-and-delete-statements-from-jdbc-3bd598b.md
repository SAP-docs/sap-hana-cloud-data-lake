<!-- loio3bd598b66c5f1014a2f3cc609b70ff41 -->

# Using Prepared INSERT and DELETE Statements from JDBC

Call a sample JDBC application from the database server to insert and delete rows in the Departments table using prepared statements.



## Prerequisites

To create an external procedure, you must have the CREATE PROCEDURE and CREATE EXTERNAL REFERENCE system privileges. You must also have SELECT, DELETE, and INSERT privileges on the database object you are modifying.



## Procedure

1.  Connect to the sample database from Interactive SQL.

2.  Ensure the JDBCExample class has been installed.

3.  Define a stored procedure named JDBCInsert that acts as a wrapper for the JDBCExample.Insert method in the class:

    ```
    CREATE PROCEDURE JDBCInsert( IN arg1 INTEGER, IN arg2 LONG VARCHAR )
      EXTERNAL NAME 'JDBCExample.Insert(ILjava/lang/String;)V'
      LANGUAGE JAVA;
    ```

4.  Call the JDBCExample.Insert method as follows:

    ```
    CALL JDBCInsert( 202, 'Southeastern Sales' );
    ```

    The Insert method causes the InsertDynamic method to be invoked.

5.  Confirm that a row has been added to the Departments table.

    ```
    SELECT * FROM Departments;
    ```

    The example program displays the updated contents of the Departments table in the database server messages window.

6.  There is a similar method in the example class called DeleteDynamic that shows how to delete the row that has just been added.

    Define a stored procedure named JDBCDelete that acts as a wrapper for the JDBCExample.Delete method in the class:

    ```
    CREATE PROCEDURE JDBCDelete( IN arg1 INTEGER )
      EXTERNAL NAME 'JDBCExample.Delete(I)V'
      LANGUAGE JAVA;
    ```

7.  Call the JDBCExample.Delete method as follows:

    ```
    CALL JDBCDelete( 202 );
    ```

    The Delete method causes the DeleteDynamic method to be invoked.

8.  Confirm that the row has been deleted from the Departments table.

    ```
    SELECT * FROM Departments;
    ```

    The updated contents of the Departments table are displayed.




## Results

Rows are inserted and deleted from a table using prepared SQL statements in a server-side JDBC application. The updated contents of the Departments table are displayed in the database server messages window.

