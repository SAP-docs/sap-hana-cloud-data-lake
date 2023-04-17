<!-- loio3bd378196c5f10149d41c585b0a4b6d4 -->

# Returning Result Sets from JDBC

Call a sample JDBC application from the database server to return several result sets.



## Prerequisites

To create an external procedure, you must have the CREATE PROCEDURE and CREATE EXTERNAL REFERENCE system privileges. You must also have SELECT, DELETE, and INSERT privileges on the database object you are modifying.



## Procedure

1.  Connect to the sample database from Interactive SQL.

2.  Ensure the JDBCExample class has been installed.

3.  Define a stored procedure named JDBCResults that acts as a wrapper for the JDBCExample.Results method in the class.

    For example:

    ```
    CREATE PROCEDURE JDBCResults(OUT args LONG VARCHAR)
      DYNAMIC RESULT SETS 3
      EXTERNAL NAME 'JDBCExample.Results([Ljava/sql/ResultSet;)V'
      LANGUAGE JAVA;
    ```

    The example returns 3 result sets.

4.  Set the following Interactive SQL options so you can see all the results of the query:

    1.  Click *Tools* \> *Options*.

    2.  Click ****.

    3.  Click the *Results* tab.

    4.  Set the value for *Maximum Number Of Rows To Display* to ***5000***.

    5.  Click *OK*.


5.  Call the JDBCExample.Results method.

    ```
    CALL JDBCResults();
    ```

6.  Check each of the three results tabs, *Result Set 1*, *Result Set 2*, and *Result Set 3*.




## Results

Three different result sets are returned from a server-side JDBC application.

