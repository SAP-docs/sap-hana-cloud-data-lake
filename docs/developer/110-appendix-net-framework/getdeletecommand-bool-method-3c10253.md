<!-- loio3c1025366c5f1014bdd195b67e03f144 -->

# GetDeleteCommand\(bool\) Method

Returns the generated SACommand object that performs DELETE operations on the database when SADataAdapter.Update is called.



Visual Basic
:   ```
Public Shadows Function GetDeleteCommand (ByVal useColumnsForParameterNames As Boolean) As SACommand
```

C\#
:   ```
public new SACommand GetDeleteCommand (bool useColumnsForParameterNames)
```



## Parameters

useColumnsForParameterNames
:   If true, then generate parameter names matching column names if possible. If false, then generate @p1, @p2, and so on.



## Returns

The automatically generated SACommand object required to perform deletions.



## Remarks

The GetDeleteCommand method returns the SACommand object to be executed, so it is useful for informational or troubleshooting purposes.

Alternatively, use GetDeleteCommand as the basis of a modified command. For example, you might call GetDeleteCommand and modify the CommandTimeout value, and then explicitly set that value on the SADataAdapter.

SQL statements are first generated when the application calls Update or GetDeleteCommand. After the SQL statement is first generated, the application must explicitly call RefreshSchema if it changes the statement in any way. Otherwise, the GetDeleteCommand continues to use information from the previous statement.

