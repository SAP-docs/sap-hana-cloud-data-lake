<!-- loio8166878b6ce210148c9bdecf9967b487 -->

# Executing Prepared Statements

Execute prepared statements to provide performance advantages for statements that are used repeatedly.



## Prerequisites

To run the example successfully, you need the following system privileges.

-   INSERT on the Departments table




## Procedure

1.  Prepare the statement using SQLPrepare.

    For example, the following code fragment illustrates how to prepare an INSERT statement:

    ```
    rc = SQLPrepare( stmt,
        "INSERT INTO Departments( DepartmentID, DepartmentName, DepartmentHeadID ) "
        "VALUES (?, ?, ?)",
        SQL_NTS );
    ```

    In this example:

    rc
    :   Receives a return code that should be tested for success or failure of the operation.

    stmt
    :   Provides a handle to the statement so that it can be referenced later.

    ?
    :   The question marks are placeholders for statement parameters. A placeholder is put in the statement to indicate where host variables are to be accessed. A placeholder is either a question mark \(?\) or a host variable reference \(a host variable name preceded by a colon\). In the latter case, the host variable name used in the actual text of the statement serves only as a placeholder indicating that a corresponding parameter is to be bound to it. It need not match the actual parameter name.

2.  Bind statement parameter values using SQLBindParameter.

    For example, the following function call binds the value of the DepartmentID variable:

    ```
    rc = SQLBindParameter( stmt,
                     1,
                     SQL_PARAM_INPUT,
                     SQL_C_SSHORT,
                     SQL_INTEGER,
                     0,
                     0,
                     &sDeptID,
                     0,
                     &cbDeptID );
    ```

    In this example:

    rc
    :   Holds a return code that should be tested for success or failure of the operation.

    stmt
    :   is the statement handle.

    1
    :   indicates that this call sets the value of the first placeholder.

    SQL\_PARAM\_INPUT
    :   indicates that the parameter is an input statement.

    SQL\_C\_SHORT
    :   indicates the C data type being used in the application.

    SQL\_INTEGER
    :   indicates SQL data type being used in the database.

        The next two parameters indicate the column precision and the number of decimal digits: both zero for integers.

    &sDeptID
    :   is a pointer to a buffer for the parameter value.

    0
    :   indicates the length of the buffer, in bytes.

    &cbDeptID
    :   is a pointer to a buffer for the length of the parameter value.

3.  Bind the other two parameters and assign values to sDeptId.

4.  Execute the statement:

    ```
    rc = SQLExecute( stmt );
    ```

    Steps 2 to 4 can be carried out multiple times.

5.  Drop the statement.

    Dropping the statement frees resources associated with the statement itself. You drop statements using SQLFreeHandle.




## Results

When built and run, the application executes the prepared statements.



## Next Steps

The above code fragments do not include error checking. For a complete sample, including error checking, see <code><i>%IQDIRSAMP17%</i>\SQLAnywhere\ODBCPrepare\odbcprepare.cpp</code>.

