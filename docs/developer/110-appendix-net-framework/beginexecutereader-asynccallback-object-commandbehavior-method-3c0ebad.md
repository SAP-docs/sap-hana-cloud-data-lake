<!-- loio3c0ebad86c5f10148107b9c04974199f -->

# BeginExecuteReader\(AsyncCallback, object, CommandBehavior\) Method

Initiates the asynchronous execution of a SQL statement or stored procedure that is described by this SACommand, and retrieves one or more result sets from the database server.



Visual Basic
:   ```
Public Function BeginExecuteReader (
    ByVal callback As AsyncCallback,
    ByVal stateObject As Object,
    ByVal behavior As CommandBehavior
) As IAsyncResult
```

C\#
:   ```
public IAsyncResult BeginExecuteReader (
    AsyncCallback callback,
    object stateObject,
    CommandBehavior behavior
)
```



## Parameters

callback
:   A System.AsyncCallback delegate that is invoked when the command's execution has completed. Pass null \(Nothing in Microsoft Visual Basic\) to indicate that no callback is required.

stateObject
:   A user-defined state object that is passed to the callback procedure. Retrieve this object from within the callback procedure using the System.IAsyncResult.AsyncState property.

behavior
:   A bitwise combination of System.Data.CommandBehavior flags describing the results of the query and its effect on the connection.



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

