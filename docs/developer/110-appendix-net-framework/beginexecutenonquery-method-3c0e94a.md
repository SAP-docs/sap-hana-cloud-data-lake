<!-- loio3c0e94a86c5f1014b102e3663367660d -->

# BeginExecuteNonQuery\(\) Method

Initiates the asynchronous execution of a SQL statement or stored procedure that is described by this SACommand.



Visual Basic
:   ```
Public Function BeginExecuteNonQuery () As IAsyncResult
```

C\#
:   ```
public IAsyncResult BeginExecuteNonQuery ()
```



## Returns

A System.IAsyncResult that can be used to poll, wait for results, or both; this value is also needed when invoking EndExecuteNonQuery\(IAsyncResult\), which returns the number of affected rows.



## Exceptions

SAException class
:   Any error that occurred while executing the command text.



## Remarks

For asynchronous command, the order of parameters must be consistent with CommandText.

**Related Information**  


[EndExecuteNonQuery\(IAsyncResult\) Method](endexecutenonquery-iasyncresult-method-3c0f3f9.md "Finishes asynchronous execution of a SQL statement or stored procedure.")

