<!-- loio3bd672146c5f1014aa9aaa5a43294cd1 -->

# Stored Procedure Considerations

You can create and call stored procedures and process the results from an ODBC application.



## Procedures and Result Sets

There are two types of procedures: those that return result sets and those that do not. You can use SQLNumResultCols to tell the difference: the number of result columns is zero if the procedure does not return a result set. If there is a result set, you can fetch the values using SQLFetch or SQLExtendedFetch just like any other cursor.

Parameters to procedures should be passed using parameter markers \(question marks\). Use SQLBindParameter to assign a storage area for each parameter marker, whether it is an INPUT, OUTPUT, or INOUT parameter.

To handle multiple result sets, ODBC must describe the currently executing cursor, not the procedure-defined result set. Therefore, ODBC does not always describe column names as defined in the RESULT clause of the stored procedure definition. To avoid this problem, you can use column aliases in your procedure result set cursor.



Example 1
:   This example creates and calls a procedure that does not return a result set. The procedure takes one INOUT parameter, and increments its value. In the example, the variable `num_columns` has the value zero, since the procedure does not return a result set. Error checking has been omitted to make the example easier to read.

    ```
    HDBC dbc;
    SQLHSTMT stmt;
    SQLINTEGER I;
    SQLSMALLINT num_columns;
    
    SQLAllocStmt( dbc, &stmt );
    SQLExecDirect( stmt,
        "CREATE PROCEDURE Increment( INOUT a INT )" 
        "BEGIN " 
        "    SET a = a + 1 " 
        "END", SQL_NTS ); 
    
    /* Call the procedure to increment 'I' */
    I = 1;
    SQLBindParameter( stmt, 1, SQL_C_LONG, SQL_INTEGER, 0, 0, &I, NULL );
    SQLExecDirect( stmt, "CALL Increment( ? )", SQL_NTS );
    SQLNumResultCols( stmt, &num_columns );
    ```

Example 2
:   This example calls a procedure that returns a result set. In the example, the variable `num_columns` will have the value 2 since the procedure returns a result set with two columns. Again, error checking has been omitted to make the example easier to read.

    ```
    SQLRETURN rc;
    SQLHDBC dbc;
    SQLHSTMT stmt;
    SQLSMALLINT num_columns;
    
    SQLCHAR ID[ 10 ];
    SQLCHAR Surname[ 20 ]; 
    
    SQLExecDirect( stmt,
          "CREATE PROCEDURE EmployeeList() "
          "RESULT( ID CHAR(10), Surname CHAR(20) ) "
          "BEGIN "
          "    SELECT EmployeeID, Surname FROM Employees "
          "END", SQL_NTS );
    
    /* Call the procedure - print the results */
    SQLExecDirect( stmt, "CALL EmployeeList()", SQL_NTS );
    SQLNumResultCols( stmt, &num_columns );
    SQLBindCol( stmt, 1, SQL_C_CHAR, &ID, sizeof(ID), NULL );
    SQLBindCol( stmt, 2, SQL_C_CHAR, &Surname, sizeof(Surname), NULL );
    
    for( ;; ) 
    {
       rc = SQLFetch( stmt );
       if( rc == SQL_NO_DATA ) 
       {
          rc = SQLMoreResults( stmt );
          if( rc == SQL_NO_DATA ) break;
       } 
       else 
       {
          do_something( ID, Surname );
       }
    }
    SQLCloseCursor( stmt );
    SQLFreeHandle( SQL_HANDLE_STMT, stmt );
    ```

