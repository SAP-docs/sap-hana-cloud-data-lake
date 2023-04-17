<!-- loio3bd937db6c5f101492ece55494692fa6 -->

# 64-bit ODBC Considerations

When you use an ODBC function like SQLBindCol, SQLBindParameter, or SQLGetData, some of the parameters are typed as SQLLEN or SQLULEN in the function prototype.



Depending on the date of the Microsoft ODBC API Reference documentation that you are looking at, you might see the same parameters described as SQLINTEGER or SQLUINTEGER.

SQLLEN and SQLULEN data items are 64 bits in a 64-bit ODBC application and 32 bits in a 32-bit ODBC application. SQLINTEGER and SQLUINTEGER data items are 32 bits on all platforms.

To illustrate the problem, the following ODBC function prototype was excerpted from an older copy of the Microsoft ODBC API Reference.

```
SQLRETURN SQLGetData(
     SQLHSTMT     StatementHandle,
     SQLUSMALLINT ColumnNumber,
     SQLSMALLINT  TargetType,
     SQLPOINTER   TargetValuePtr,
     SQLINTEGER   BufferLength,
     SQLINTEGER  *StrLen_or_IndPtr);
```

Compare this with the actual function prototype found in `sql.h` in Microsoft Visual Studio version 8.

```
SQLRETURN  SQL_API SQLGetData(
    SQLHSTMT      StatementHandle,
    SQLUSMALLINT  ColumnNumber, 
    SQLSMALLINT   TargetType,
    SQLPOINTER    TargetValue, 
    SQLLEN        BufferLength,
    SQLLEN       *StrLen_or_Ind);
```

As you can see, the BufferLength and StrLen\_or\_Ind parameters are now typed as SQLLEN, not SQLINTEGER. For the 64-bit platform, these are 64-bit quantities, not 32-bit quantities as indicated in the Microsoft documentation.

To avoid issues with cross-platform compilation, the database server software provides its own ODBC header files. For Windows platforms, include the `ntodbc.h` header file. For UNIX and Linux platforms, include the `unixodbc.h` header file. Use of these header files ensures compatibility with the corresponding ODBC driver for the target platform.

The following table lists some common ODBC types.


<table>
<tr>
<th valign="top">

ODBC API



</th>
<th valign="top">

64-bit Platform



</th>
</tr>
<tr>
<td valign="top">

SQLINTEGER



</td>
<td valign="top">

32 bits



</td>
</tr>
<tr>
<td valign="top">

SQLUINTEGER



</td>
<td valign="top">

32 bits



</td>
</tr>
<tr>
<td valign="top">

SQLLEN



</td>
<td valign="top">

64 bits



</td>
</tr>
<tr>
<td valign="top">

SQLULEN



</td>
<td valign="top">

64 bits



</td>
</tr>
<tr>
<td valign="top">

SQLSETPOSIROW



</td>
<td valign="top">

64 bits



</td>
</tr>
<tr>
<td valign="top">

SQL\_C\_BOOKMARK



</td>
<td valign="top">

64 bits



</td>
</tr>
<tr>
<td valign="top">

BOOKMARK



</td>
<td valign="top">

64 bits



</td>
</tr>
</table>

If you declare data variables and parameters incorrectly, then you may encounter incorrect software behavior.

The following table summarizes the ODBC API function prototypes that have changed with the introduction of 64-bit support. The parameters that are affected are noted. The parameter name as documented by Microsoft is shown in parentheses when it differs from the actual parameter name used in the function prototype. The parameter names are those used in the Microsoft Visual Studio version 8 header files.


<table>
<tr>
<th valign="top">

ODBC API



</th>
<th valign="top">

Parameter \(Documented Parameter Name\)



</th>
</tr>
<tr>
<td valign="top">

SQLBindCol



</td>
<td valign="top">

SQLLEN BufferLength

SQLLEN \*Strlen\_or\_Ind



</td>
</tr>
<tr>
<td valign="top">

SQLBindParam



</td>
<td valign="top">

SQLULEN LengthPrecision

SQLLEN \*Strlen\_or\_Ind



</td>
</tr>
<tr>
<td valign="top">

SQLBindParameter



</td>
<td valign="top">

SQLULEN cbColDef \(ColumnSize\)

SQLLEN cbValueMax \(BufferLength\)

SQLLEN \*pcbValue \(Strlen\_or\_IndPtr\)



</td>
</tr>
<tr>
<td valign="top">

SQLColAttribute



</td>
<td valign="top">

SQLLEN \*NumericAttribute



</td>
</tr>
<tr>
<td valign="top">

SQLColAttributes



</td>
<td valign="top">

SQLLEN \*pfDesc



</td>
</tr>
<tr>
<td valign="top">

SQLDescribeCol



</td>
<td valign="top">

SQLULEN \*ColumnSize \(ColumnSizePtr\)



</td>
</tr>
<tr>
<td valign="top">

SQLDescribeParam



</td>
<td valign="top">

SQLULEN \*pcbParamDef \(ParameterSizePtr\)



</td>
</tr>
<tr>
<td valign="top">

SQLExtendedFetch



</td>
<td valign="top">

SQLLEN irow \(FetchOffset\)

SQLULEN \*pcrow \(RowCountPtr\)



</td>
</tr>
<tr>
<td valign="top">

SQLFetchScroll



</td>
<td valign="top">

SQLLEN FetchOffset



</td>
</tr>
<tr>
<td valign="top">

SQLGetData



</td>
<td valign="top">

SQLLEN BufferLength

SQLLEN \*Strlen\_or\_Ind \(Strlen\_or\_IndPtr\)



</td>
</tr>
<tr>
<td valign="top">

SQLGetDescRec



</td>
<td valign="top">

SQLLEN \*Length \(LengthPtr\)



</td>
</tr>
<tr>
<td valign="top">

SQLParamOptions



</td>
<td valign="top">

SQLULEN crow,

SQLULEN \*pirow



</td>
</tr>
<tr>
<td valign="top">

SQLPutData



</td>
<td valign="top">

SQLLEN Strlen\_or\_Ind



</td>
</tr>
<tr>
<td valign="top">

SQLRowCount



</td>
<td valign="top">

SQLLEN \*RowCount \(RowCountPtr\)



</td>
</tr>
<tr>
<td valign="top">

SQLSetConnectOption



</td>
<td valign="top">

SQLULEN Value



</td>
</tr>
<tr>
<td valign="top">

SQLSetDescRec



</td>
<td valign="top">

SQLLEN Length

SQLLEN \*StringLength \(StringLengthPtr\)

SQLLEN \*Indicator \(IndicatorPtr\)



</td>
</tr>
<tr>
<td valign="top">

SQLSetParam



</td>
<td valign="top">

SQLULEN LengthPrecision

SQLLEN \*Strlen\_or\_Ind \(Strlen\_or\_IndPtr\)



</td>
</tr>
<tr>
<td valign="top">

SQLSetPos



</td>
<td valign="top">

SQLSETPOSIROW irow \(RowNumber\)



</td>
</tr>
<tr>
<td valign="top">

SQLSetScrollOptions



</td>
<td valign="top">

SQLLEN crowKeyset



</td>
</tr>
<tr>
<td valign="top">

SQLSetStmtOption



</td>
<td valign="top">

SQLULEN Value



</td>
</tr>
</table>

Some values passed into and returned from ODBC API calls through pointers have changed to accommodate 64-bit applications. For example, the following values for the SQLSetStmtAttr and SQLSetDescField functions are no longer SQLINTEGER/SQLUINTEGER. The same rule applies to the corresponding parameters for the SQLGetStmtAttr and SQLGetDescField functions.


<table>
<tr>
<th valign="top">

ODBC API



</th>
<th valign="top">

Type for Value/ValuePtr Variable



</th>
</tr>
<tr>
<td valign="top">

SQLSetStmtAttr\(SQL\_ATTR\_FETCH\_BOOKMARK\_PTR\)



</td>
<td valign="top">

SQLLEN \* value



</td>
</tr>
<tr>
<td valign="top">

SQLSetStmtAttr\(SQL\_ATTR\_KEYSET\_SIZE\)



</td>
<td valign="top">

SQLULEN value



</td>
</tr>
<tr>
<td valign="top">

SQLSetStmtAttr\(SQL\_ATTR\_MAX\_LENGTH\)



</td>
<td valign="top">

SQLULEN value



</td>
</tr>
<tr>
<td valign="top">

SQLSetStmtAttr\(SQL\_ATTR\_MAX\_ROWS\)



</td>
<td valign="top">

SQLULEN value



</td>
</tr>
<tr>
<td valign="top">

SQLSetStmtAttr\(SQL\_ATTR\_PARAM\_BIND\_OFFSET\_PTR\)



</td>
<td valign="top">

SQLULEN \* value



</td>
</tr>
<tr>
<td valign="top">

SQLSetStmtAttr\(SQL\_ATTR\_PARAMS\_PROCESSED\_PTR\)



</td>
<td valign="top">

SQLULEN \* value



</td>
</tr>
<tr>
<td valign="top">

SQLSetStmtAttr\(SQL\_ATTR\_PARAMSET\_SIZE\)



</td>
<td valign="top">

SQLULEN value



</td>
</tr>
<tr>
<td valign="top">

SQLSetStmtAttr\(SQL\_ATTR\_ROW\_ARRAY\_SIZE\)



</td>
<td valign="top">

SQLULEN value



</td>
</tr>
<tr>
<td valign="top">

SQLSetStmtAttr\(SQL\_ATTR\_ROW\_BIND\_OFFSET\_PTR\)



</td>
<td valign="top">

SQLULEN \* value



</td>
</tr>
<tr>
<td valign="top">

SQLSetStmtAttr\(SQL\_ATTR\_ROW\_NUMBER\)



</td>
<td valign="top">

SQLULEN value



</td>
</tr>
<tr>
<td valign="top">

SQLSetStmtAttr\(SQL\_ATTR\_ROWS\_FETCHED\_PTR\)



</td>
<td valign="top">

SQLULEN \* value



</td>
</tr>
<tr>
<td valign="top">

SQLSetDescField\(SQL\_DESC\_ARRAY\_SIZE\)



</td>
<td valign="top">

SQLULEN value



</td>
</tr>
<tr>
<td valign="top">

SQLSetDescField\(SQL\_DESC\_BIND\_OFFSET\_PTR\)



</td>
<td valign="top">

SQLLEN \* value



</td>
</tr>
<tr>
<td valign="top">

SQLSetDescField\(SQL\_DESC\_ROWS\_PROCESSED\_PTR\)



</td>
<td valign="top">

SQLULEN \* value



</td>
</tr>
<tr>
<td valign="top">

SQLSetDescField\(SQL\_DESC\_DISPLAY\_SIZE\)



</td>
<td valign="top">

SQLLEN value



</td>
</tr>
<tr>
<td valign="top">

SQLSetDescField\(SQL\_DESC\_INDICATOR\_PTR\)



</td>
<td valign="top">

SQLLEN \* value



</td>
</tr>
<tr>
<td valign="top">

SQLSetDescField\(SQL\_DESC\_LENGTH\)



</td>
<td valign="top">

SQLLEN value



</td>
</tr>
<tr>
<td valign="top">

SQLSetDescField\(SQL\_DESC\_OCTET\_LENGTH\)



</td>
<td valign="top">

SQLLEN value



</td>
</tr>
<tr>
<td valign="top">

SQLSetDescField\(SQL\_DESC\_OCTET\_LENGTH\_PTR\)



</td>
<td valign="top">

SQLLEN \* value



</td>
</tr>
</table>

