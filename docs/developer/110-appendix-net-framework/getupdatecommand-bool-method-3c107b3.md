<!-- loio3c107b3e6c5f10148d9ba5f236cdeb3e -->

# GetUpdateCommand\(bool\) Method

Returns the generated SACommand object that performs UPDATE operations on the database when an Update is called.



Visual Basic
:   ```
Public Shadows Function GetUpdateCommand (ByVal useColumnsForParameterNames As Boolean) As SACommand
```

C\#
:   ```
public new SACommand GetUpdateCommand (bool useColumnsForParameterNames)
```



## Parameters

useColumnsForParameterNames
:   If true, then generate parameter names matching column names if possible. If false, then generate @p1, @p2, and so on.



## Returns

The automatically generated SACommand object required to perform updates.



## Remarks

The GetUpdateCommand method returns the SACommand object to be executed, so it is useful for informational or troubleshooting purposes.

Alternatively, use GetUpdateCommand as the basis of a modified command. For example, you might call GetUpdateCommand and modify the CommandTimeout value, and then explicitly set that value on the SADataAdapter.

SQL statements are first generated when the application calls Update or GetUpdateCommand. After the SQL statement is first generated, the application must explicitly call RefreshSchema if it changes the statement in any way. Otherwise, the GetUpdateCommand continues to use information from the previous statement, which might not be correct.

