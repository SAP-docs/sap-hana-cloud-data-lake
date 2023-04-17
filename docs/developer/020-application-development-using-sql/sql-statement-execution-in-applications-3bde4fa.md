<!-- loio3bde4fa66c5f1014b962f8e13704fd89 -->

# SQL Statement Execution in Applications

The way you include SQL statements in your application depends on the application development tool and programming interface you use.

ADO.NET
:   You can execute SQL statements using various ADO.NET objects. The SACommand object is one example:

    ```
    SACommand cmd = new SACommand(
         "DELETE FROM Employees WHERE EmployeeID = 105", conn );
    cmd.ExecuteNonQuery();
    ```

ODBC
:   If you are writing directly to the ODBC programming interface, your SQL statements appear in function calls. For example, the following C function call executes a DELETE statement:

    ```
    SQLExecDirect( stmt,
        "DELETE FROM Employees
         WHERE EmployeeID = 105",
        SQL_NTS );
    ```

JDBC
:   If you are using the JDBC programming interface, you can execute SQL statements by invoking methods of the statement object. For example:

    ```
    stmt.executeUpdate(
        "DELETE FROM Employees
         WHERE EmployeeID = 105" );
    ```

Embedded SQL
:   If you are using Embedded SQL, you prefix your C language SQL statements with the keyword EXEC SQL. The code is then run through a preprocessor before compiling. For example:

    ```
    EXEC SQL EXECUTE IMMEDIATE
     'DELETE FROM Employees
      WHERE EmployeeID = 105';
    ```

SAP Open Client
:   If you use the SAP Open Client interface, your SQL statements appear in function calls. For example, the following pair of calls executes a DELETE statement:

    ```
    ret = ct_command( cmd, CS_LANG_CMD,
                      "DELETE FROM Employees
                       WHERE EmployeeID=105"
                     CS_NULLTERM,
                     CS_UNUSED);
    ret = ct_send(cmd);
    ```

For more details about including SQL in your application, see your development tool documentation. If you are using ODBC or JDBC, consult the software development kit for those interfaces.



## Applications Inside the Database Server

In many ways, stored procedures and triggers act as applications or parts of applications running inside the database server. You can also use many of the techniques here in stored procedures.

Java classes in the database can use the JDBC interface in the same way as Java applications outside the server.

