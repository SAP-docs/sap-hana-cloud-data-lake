<!-- loio81df76966ce210149685b03b286a457c -->

# ExecuteReaderAsync\(CommandBehavior, CancellationToken\) Method

An asynchronous version of SACommand.ExecuteReader, which Executes a SQL statement that returns a result set.



Visual Basic
:   ```
Public Shadows Function ExecuteReaderAsync (
    ByVal behavior As CommandBehavior,
    ByVal cancellationToken As CancellationToken
) As Task< SADataReader >
```

C\#
:   ```
public new Task< SADataReader > ExecuteReaderAsync (
    CommandBehavior behavior,
    CancellationToken cancellationToken
)
```



## Parameters

behavior
:   Options for statement execution and data retrieval.

cancellationToken
:   The cancellation instruction.



## Returns

A task representing the asynchronous operation.



## Exceptions

SAException class
:   The database server returned an error while executing the command text.



## Remarks

The cancellation token can be used to request that the operation be abandoned before the command timeout elapses. Exceptions are reported via the returned Task object.

