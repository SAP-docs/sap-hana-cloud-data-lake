<!-- loio3c101d546c5f1014925ec90f4abce800 -->

# GetDeleteCommand\(\) Method

Returns the generated SACommand object that performs DELETE operations on the database when SADataAdapter.Update is called.



Visual Basic
:   ```
Public Shadows Function GetDeleteCommand () As SACommand
```

C\#
:   ```
public new SACommand GetDeleteCommand ()
```



## Returns

The automatically generated SACommand object required to perform deletions.



## Remarks

The GetDeleteCommand method returns the SACommand object to be executed, so it is useful for informational or troubleshooting purposes.

Alternatively, use GetDeleteCommand as the basis of a modified command. For example, you might call GetDeleteCommand and modify the CommandTimeout value, and then explicitly set that value on the SADataAdapter.

SQL statements are first generated when the application calls Update or GetDeleteCommand. After the SQL statement is first generated, the application must explicitly call RefreshSchema if it changes the statement in any way. Otherwise, the GetDeleteCommand continues to use information from the previous statement.

