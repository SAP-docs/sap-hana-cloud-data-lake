<!-- loio3c103d096c5f1014968ba0bac5a07471 -->

# GetInsertCommand\(bool\) Method

Returns the generated SACommand object that performs INSERT operations on the database when an Update is called.



Visual Basic
:   ```
Public Shadows Function GetInsertCommand (ByVal useColumnsForParameterNames As Boolean) As SACommand
```

C\#
:   ```
public new SACommand GetInsertCommand (bool useColumnsForParameterNames)
```



## Parameters

useColumnsForParameterNames
:   If true, then generate parameter names matching column names if possible. If false, then generate @p1, @p2, and so on.



## Returns

The automatically generated SACommand object required to perform insertions.



## Remarks

The GetInsertCommand method returns the SACommand object to be executed, so it is useful for informational or troubleshooting purposes.

Alternatively, use GetInsertCommand as the basis of a modified command. For example, you might call GetInsertCommand and modify the CommandTimeout value, and then explicitly set that value on the SADataAdapter.

SQL statements are first generated either when the application calls Update or GetInsertCommand. After the SQL statement is first generated, the application must explicitly call RefreshSchema if it changes the statement in any way. Otherwise, the GetInsertCommand continues to use information from the previous statement, which might not be correct.

**Related Information**  


[GetDeleteCommand\(\) Method](getdeletecommand-method-3c101d5.md "Returns the generated SACommand object that performs DELETE operations on the database when SADataAdapter.Update is called.")

