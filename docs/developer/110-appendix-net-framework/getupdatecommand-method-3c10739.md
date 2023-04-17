<!-- loio3c10739a6c5f1014b45889ade33dc0e9 -->

# GetUpdateCommand\(\) Method

Returns the generated SACommand object that performs UPDATE operations on the database when an Update is called.



Visual Basic
:   ```
Public Shadows Function GetUpdateCommand () As SACommand
```

C\#
:   ```
public new SACommand GetUpdateCommand ()
```



## Returns

The automatically generated SACommand object required to perform updates.



## Remarks

The GetUpdateCommand method returns the SACommand object to be executed, so it is useful for informational or troubleshooting purposes.

Alternatively, use GetUpdateCommand as the basis of a modified command. For example, you might call GetUpdateCommand and modify the CommandTimeout value, and then explicitly set that value on the SADataAdapter.

SQL statements are first generated when the application calls Update or GetUpdateCommand. After the SQL statement is first generated, the application must explicitly call RefreshSchema if it changes the statement in any way. Otherwise, the GetUpdateCommand continues to use information from the previous statement, which might not be correct.

