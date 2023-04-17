<!-- loio81df69ae6ce210149dc8ec92702a57ae -->

# ExecuteReaderAsync\(CommandBehavior\) Method

An asynchronous version of SACommand.ExecuteReader, which Executes a SQL statement that returns a result set.



Visual Basic
:   ```
Public Shadows Function ExecuteReaderAsync (ByVal behavior As CommandBehavior) As Task< SADataReader >
```

C\#
:   ```
public new Task< SADataReader > ExecuteReaderAsync (CommandBehavior behavior)
```



## Parameters

behavior
:   Options for statement execution and data retrieval.



## Returns

A task representing the asynchronous operation.



## Exceptions

SAException class
:   The database server returned an error while executing the command text.



## Remarks

Exceptions are reported via the returned Task object.

