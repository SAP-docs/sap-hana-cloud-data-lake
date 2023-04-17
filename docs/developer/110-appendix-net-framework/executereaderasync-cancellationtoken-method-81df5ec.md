<!-- loio81df5ec86ce2101483f8a0570f9516d8 -->

# ExecuteReaderAsync\(CancellationToken\) Method

An asynchronous version of SACommand.ExecuteReader, which Executes a SQL statement that returns a result set.



Visual Basic
:   ```
Public Shadows Function ExecuteReaderAsync (ByVal cancellationToken As CancellationToken) As Task< SADataReader >
```

C\#
:   ```
public new Task< SADataReader > ExecuteReaderAsync (CancellationToken cancellationToken)
```



## Parameters

cancellationToken
:   The cancellation instruction.



## Returns

A task representing the asynchronous operation.



## Exceptions

SAException class
:   The database server returned an error while executing the command text.



## Remarks

The cancellation token can be used to request that the operation be abandoned before the command timeout elapses. Exceptions are reported via the returned Task object.

