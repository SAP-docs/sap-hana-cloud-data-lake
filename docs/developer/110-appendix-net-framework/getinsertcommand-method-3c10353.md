<!-- loio3c1035386c5f10149e7c828f39bd6a4c -->

# GetInsertCommand\(\) Method

Returns the generated SACommand object that performs INSERT operations on the database when an Update is called.



Visual Basic
:   ```
Public Shadows Function GetInsertCommand () As SACommand
```

C\#
:   ```
public new SACommand GetInsertCommand ()
```



## Returns

The automatically generated SACommand object required to perform insertions.



## Remarks

The GetInsertCommand method returns the SACommand object to be executed, so it is useful for informational or troubleshooting purposes.

Alternatively, use GetInsertCommand as the basis of a modified command. For example, you might call GetInsertCommand and modify the CommandTimeout value, and then explicitly set that value on the SADataAdapter.

SQL statements are first generated either when the application calls Update or GetInsertCommand. After the SQL statement is first generated, the application must explicitly call RefreshSchema if it changes the statement in any way. Otherwise, the GetInsertCommand continues to use information from the previous statement, which might not be correct.

**Related Information**  


[GetDeleteCommand\(\) Method](getdeletecommand-method-3c101d5.md "Returns the generated SACommand object that performs DELETE operations on the database when SADataAdapter.Update is called.")
