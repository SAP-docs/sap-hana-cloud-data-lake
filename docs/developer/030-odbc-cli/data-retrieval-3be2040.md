<!-- loio3be204046c5f10148dd7eb7187101a02 -->

# Data Retrieval

To retrieve rows from a database, you execute a SELECT statement using SQLExecute or SQLExecDirect. This opens a cursor on the statement.

You then use SQLFetch or SQLFetchScroll to fetch rows through the cursor. These functions fetch the next rowset of data from the result set and return data for all bound columns. Using SQLFetchScroll, rowsets can be specified at an absolute or relative position or by bookmark. SQLFetchScroll replaces the older SQLExtendedFetch from the ODBC 2.0 specification.

When an application frees the statement using SQLFreeHandle, it closes the cursor.

To fetch values from a cursor, your application can use either SQLBindCol or SQLGetData. If you use SQLBindCol, values are automatically retrieved on each fetch. If you use SQLGetData, you must call it for each column after each fetch.

SQLGetData is used to fetch values in pieces for columns such as LONG VARCHAR or LONG BINARY. As an alternative, you can set the SQL\_ATTR\_MAX\_LENGTH statement attribute to a value large enough to hold the entire value for the column. The default value for SQL\_ATTR\_MAX\_LENGTH is 256 KB.

The ODBC driver implements SQL\_ATTR\_MAX\_LENGTH in a different way than intended by the ODBC specification. The intended meaning for SQL\_ATTR\_MAX\_LENGTH is that it be used as a mechanism to truncate large fetches. This might be done for a "preview" mode where only the first part of the data is displayed. For example, instead of transmitting a 4 MB blob from the server to the client application, only the first 500 bytes of it might be transmitted \(by setting SQL\_ATTR\_MAX\_LENGTH to 500\). The ODBC driver does not support this implementation.

When you use SQLBindCol to bind a NUMERIC or DECIMAL column to a SQL\_C\_NUMERIC target type, the data value is stored in a 128-bit field \(*val*\) of a SQL\_NUMERIC\_STRUCT. This field can only accommodate a maximum precision of 38. The database server supports a maximum NUMERIC precision of 127. When the precision of a NUMERIC or DECIMAL column is greater than 38, the column should be bound as SQL\_C\_CHAR to avoid loss of precision.

The following code fragment opens a cursor on a query and retrieves data through the cursor. Error checking has been omitted to make the example easier to read. The fragment is taken from a complete sample, which can be found in <code><i>%IQDIRSAMP17%</i>\SQLAnywhere\ODBCSelect\odbcselect.cpp</code>.

```
int main( int argc, char* argv[] )
{
    #define DEPT_NAME_LEN 40

    SQLLEN          cbDeptID = 0, cbDeptName = SQL_NTS, cbManagerID = 0;
    SQLCHAR         deptName[ DEPT_NAME_LEN + 1];
    SQLSMALLINT     deptID, managerID;
    SQLHENV         env;
    SQLHDBC         dbc;
    SQLHSTMT        stmt;
    SQLRETURN       retcode;

    argc = ProcessOptions( argv );
    if( argc < 0 ) return( 1 );

    retcode = SQLAllocHandle( SQL_HANDLE_ENV, SQL_NULL_HANDLE, &env );
    if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {
        /* Set the ODBC version environment attribute */
        retcode = SQLSetEnvAttr( env, SQL_ATTR_ODBC_VERSION, (void*)SQL_OV_ODBC3, 0);
        retcode = SQLAllocHandle( SQL_HANDLE_DBC, env, &dbc );
        if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {
            retcode = SQLConnect( dbc,
                    (SQLCHAR*) DataSourceName, SQL_NTS,
                    (SQLCHAR*) UserName, SQL_NTS,
                    (SQLCHAR*) Password, SQL_NTS );
            if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {
                retcode = SQLAllocHandle( SQL_HANDLE_STMT, dbc, &stmt );
                if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {
                    SQLBindCol( stmt, 1, SQL_C_SSHORT, &deptID, 0, &cbDeptID);
                    SQLBindCol( stmt, 2, SQL_C_CHAR, deptName, sizeof(deptName), &cbDeptName);
                    SQLBindCol( stmt, 3, SQL_C_SSHORT, &managerID, 0, &cbManagerID);

                    retcode = SQLExecDirect( stmt, (SQLCHAR * ) 
                            "SELECT DepartmentID, DepartmentName, DepartmentHeadID "
                            "FROM Departments "
                            "ORDER BY DepartmentID", SQL_NTS );
                    if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {
                        while( ( SQLFetch( stmt ) ) != SQL_NO_DATA ){
                            printf( "%d %20s %d\n", deptID, deptName, managerID );
                        }
                    }
                }
                SQLFreeHandle( SQL_HANDLE_STMT, stmt );
            }
            SQLDisconnect( dbc );
        }
        SQLFreeHandle( SQL_HANDLE_DBC, dbc );
    }
    SQLFreeHandle( SQL_HANDLE_ENV, env );
    return( (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) ? 0 : 1 );
}
```

The number of row positions you can fetch in a cursor is governed by the size of an integer. You can fetch rows numbered up to number 2147483646, which is one less than the value that can be held in a 32-bit integer. When using negative numbers \(rows from the end\) you can fetch down to one more than the largest negative value that can be held in an integer.

