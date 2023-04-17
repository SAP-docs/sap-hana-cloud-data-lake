<!-- loio3c0ec2736c5f1014970983517b4d578d -->

# BeginExecuteReader\(CommandBehavior\) Method

Initiates the asynchronous execution of a SQL statement or stored procedure that is described by this SACommand, and retrieves one or more result sets from the database server.



Visual Basic
:   ```
Public Function BeginExecuteReader (ByVal behavior As CommandBehavior) As IAsyncResult
```

C\#
:   ```
public IAsyncResult BeginExecuteReader (CommandBehavior behavior)
```



## Parameters

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

