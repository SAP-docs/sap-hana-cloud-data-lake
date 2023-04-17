<!-- loio3bd380246c5f1014920beb9f15b2a6d4 -->

# Using Static INSERT and DELETE Statements from JDBC

A sample JDBC application is called from the database server to insert and delete rows in the Departments table using static SQL statements.



## Prerequisites

To create an external procedure, you must have the CREATE PROCEDURE and CREATE EXTERNAL REFERENCE system privileges. You must also have SELECT, DELETE, and INSERT privileges on the database object you are modifying.



## Procedure

1.  Connect to the sample database from Interactive SQL.

2.  Ensure the JDBCExample class has been installed.

3.  Define a stored procedure named JDBCExample that acts as a wrapper for the JDBCExample.main method in the class:

    ```
    CREATE PROCEDURE JDBCExample( IN arg LONG VARCHAR )
      EXTERNAL NAME 'JDBCExample.main([Ljava/lang/String;)V'
      LANGUAGE JAVA;
    ```

4.  Call the JDBCExample.main method as follows:

    ```
    CALL JDBCExample( 'insert' );
    ```

    The argument string `'insert'` causes the InsertStatic method to be invoked.

5.  Confirm that a row has been added to the Departments table.

    ```
    SELECT * FROM Departments;
    ```

    The example program displays the updated contents of the Departments table in the database server messages window.

6.  There is a similar method in the example class called DeleteStatic that shows how to delete the row that has just been added. Call the JDBCExample.main method as follows:

    ```
    CALL JDBCExample( 'delete' );
    ```

    The argument string `'delete'` causes the DeleteStatic method to be invoked.

7.  Confirm that the row has been deleted from the Departments table.

    ```
    SELECT * FROM Departments;
    ```

    The updated contents of the Departments table are displayed.




## Results

Rows are inserted and deleted from a table using static SQL statements in a server-side JDBC application. The updated contents of the Departments table are displayed in the database server messages window.

