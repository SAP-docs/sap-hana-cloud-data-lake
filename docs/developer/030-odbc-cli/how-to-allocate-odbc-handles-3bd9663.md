<!-- loio3bd966396c5f1014a6bbebee6024463e -->

# How to Allocate ODBC Handles

ODBC defines four types of objects \(environment, connection, statement, and descriptor\) that are referenced in applications by using handles.

The handle types available for ODBC programs are as follows:


<table>
<tr>
<th valign="top">

Item



</th>
<th valign="top">

Handle Type



</th>
</tr>
<tr>
<td valign="top">

Environment



</td>
<td valign="top">

SQLHENV



</td>
</tr>
<tr>
<td valign="top">

Connection



</td>
<td valign="top">

SQLHDBC



</td>
</tr>
<tr>
<td valign="top">

Statement



</td>
<td valign="top">

SQLHSTMT



</td>
</tr>
<tr>
<td valign="top">

Descriptor



</td>
<td valign="top">

SQLHDESC



</td>
</tr>
</table>

To use an ODBC handle, you perform the following tasks:

1.  Call the SQLAllocHandle function.

2.  Use the handle in subsequent function calls.

3.  Free the object using SQLFreeHandle.


SQLAllocHandle takes the following parameters:

-   an identifier for the type of item being allocated

-   the handle of the parent item

-   a pointer to the location of the handle to be allocated


SQLFreeHandle takes the following parameters:

-   an identifier for the type of item being freed

-   the handle of the item being freed




The following code fragment allocates and frees an environment handle:

```
SQLRETURN rc;
SQLHENV env;
rc = SQLAllocHandle( SQL_HANDLE_ENV, SQL_NULL_HANDLE, &env ); 
if( rc == SQL_SUCCESS || rc == SQL_SUCCESS_WITH_INFO ) 
{
    .
    .
    .
}
SQLFreeHandle( SQL_HANDLE_ENV, env );
```

