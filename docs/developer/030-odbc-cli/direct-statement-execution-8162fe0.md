<!-- loio8162fe076ce21014b8a09e6f1fd296b5 -->

# Direct Statement Execution

To execute a SQL statement in an ODBC application, allocate a handle for the statement using SQLAllocHandle and then call the SQLExecDirect function to execute the statement.

Any parameters must be included as part of the statement \(for example, a WHERE clause must specify its arguments\). Alternatively, you can also construct statements using bound parameters.

The SQLExecDirect function takes a statement handle, a SQL string, and a length or termination indicator, which in this case is a null-terminated string indicator. The statement may include parameters.

For a complete sample with error checking, see <code><i>%IQDIRSAMP17%</i>\SQLAnywhere\ODBCExecute\odbcexecute.cpp</code>.



The following example illustrates how to allocate a handle of type SQL\_HANDLE\_STMT named stmt on a connection with handle dbc:

```
SQLAllocHandle( SQL_HANDLE_STMT, dbc, &stmt );
```

The following example illustrates how to declare a statement and execute it:

```
SQLCHAR deletestmt[ STMT_LEN ] =
  "DELETE FROM Departments WHERE DepartmentID = 201";
SQLExecDirect( stmt, deletestmt, SQL_NTS) ;
```

The deletestmt declaration should usually occur at the beginning of the function.

