<!-- loio3c0e9c526c5f1014b1ee9264a7ddc29f -->

# BeginExecuteNonQuery\(AsyncCallback, object\) Method

Initiates the asynchronous execution of a SQL statement or stored procedure that is described by this SACommand, given a callback procedure and state information.



Visual Basic
:   ```
Public Function BeginExecuteNonQuery (
    ByVal callback As AsyncCallback,
    ByVal stateObject As Object
) As IAsyncResult
```

C\#
:   ```
public IAsyncResult BeginExecuteNonQuery (
    AsyncCallback callback,
    object stateObject
)
```



## Parameters

callback
:   A System.AsyncCallback delegate that is invoked when the command's execution has completed. Pass null \(Nothing in Microsoft Visual Basic\) to indicate that no callback is required.

stateObject
:   A user-defined state object that is passed to the callback procedure. Retrieve this object from within the callback procedure using the System.IAsyncResult.AsyncState property.



## Returns

A System.IAsyncResult that can be used to poll, wait for results, or both; this value is also needed when invoking EndExecuteNonQuery\(IAsyncResult\), which returns the number of affected rows.



## Exceptions

SAException class
:   Any error that occurred while executing the command text.



## Remarks

For asynchronous command, the order of parameters must be consistent with CommandText.

**Related Information**  


[EndExecuteNonQuery\(IAsyncResult\) Method](endexecutenonquery-iasyncresult-method-3c0f3f9.md "Finishes asynchronous execution of a SQL statement or stored procedure.")

