<!-- loio3c0eb3316c5f1014823a8026ae64b230 -->

# BeginExecuteReader\(AsyncCallback, object\) Method

Initiates the asynchronous execution of a SQL statement that is described by the SACommand object, and retrieves the result set, given a callback procedure and state information.



Visual Basic
:   ```
Public Function BeginExecuteReader (
    ByVal callback As AsyncCallback,
    ByVal stateObject As Object
) As IAsyncResult
```

C\#
:   ```
public IAsyncResult BeginExecuteReader (
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

A System.IAsyncResult that can be used to poll, wait for results, or both; this value is also needed when invoking EndExecuteReader\(IAsyncResult\), which returns an SADataReader object that can be used to retrieve the returned rows.



## Exceptions

SAException class
:   Any error that occurred while executing the command text.



## Remarks

For asynchronous command, the order of parameters must be consistent with CommandText.

**Related Information**  


[EndExecuteReader\(IAsyncResult\) Method](endexecutereader-iasyncresult-method-3c0f477.md "Finishes asynchronous execution of a SQL statement or stored procedure, returning the requested SADataReader.")

[SADataReader Class](sadatareader-class-3c181c1.md "A read-only, forward-only result set from a query or stored procedure.")

