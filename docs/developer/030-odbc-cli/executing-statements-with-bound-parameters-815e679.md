<!-- loio815e679c6ce210149fc1dfd976caa36a -->

# Executing Statements with Bound Parameters

Construct and execute SQL statements using bound parameters to set values for statement parameters at runtime.



## Prerequisites

To run the example successfully, you need the following system privileges.

-   INSERT on the Departments table




## Context

Bound parameters are used with prepared statements to provide performance benefits for statements that are executed more than once.



## Procedure

1.  Allocate a handle for the statement using SQLAllocHandle.

    For example, the following statement allocates a handle of type `SQL_HANDLE_STMT` with name `stmt`, on a connection with handle `dbc`:

    ```
    SQLAllocHandle( SQL_HANDLE_STMT, dbc, &stmt );
    ```

2.  Bind parameters for the statement using SQLBindParameter.

    For example, the following lines declare variables to hold the values for the department ID, department name, and manager ID, and for the statement string. They then bind parameters to the first, second, and third parameters of a statement executed using the stmt statement handle.

    ```
    #defined DEPT_NAME_LEN 40
    SQLLEN cbDeptID = 0, cbDeptName = SQL_NTS, cbManagerID = 0;
    SQLSMALLINT deptID, managerID;
    SQLCHAR deptName[ DEPT_NAME_LEN + 1 ];
    
    SQLCHAR insertstmt[ STMT_LEN ] =
      "INSERT INTO Departments "
      "( DepartmentID, DepartmentName, DepartmentHeadID ) "
      "VALUES (?, ?, ?)"; 
    
    SQLBindParameter( stmt, 1, SQL_PARAM_INPUT,
        SQL_C_SSHORT, SQL_INTEGER, 0, 0,
        &deptID, 0, &cbDeptID );
    SQLBindParameter( stmt, 2, SQL_PARAM_INPUT,
        SQL_C_CHAR, SQL_CHAR, DEPT_NAME_LEN, 0,
        deptName, 0,&cbDeptName );
    SQLBindParameter( stmt, 3, SQL_PARAM_INPUT,
        SQL_C_SSHORT, SQL_INTEGER, 0, 0,
        &managerID, 0, &cbManagerID );
    ```

3.  Assign values to the parameters.

    For example, the following lines assign values to the parameters for the fragment of step 2.

    ```
    deptID = 201;
    strcpy( (char * ) deptName, "Sales East" );
    managerID = 902;
    ```

    Commonly, these variables would be set in response to user action.

4.  Execute the statement using SQLExecDirect.

    For example, the following line executes the statement string held in `insertstmt` on the statement handle `stmt`.

    ```
    SQLExecDirect( stmt, insertstmt, SQL_NTS );
    ```




## Results

When built and run, the application executes the SQL statement.



## Next Steps

The above code fragments do not include error checking. For a complete sample, including error checking, see <code><i>%IQDIRSAMP17%</i>\SQLAnywhere\ODBCExecute\odbcexecute.cpp</code>.

