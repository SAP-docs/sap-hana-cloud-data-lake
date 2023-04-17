<!-- loio81df53bc6ce2101493e088fce6ab7eb2 -->

# ExecuteReaderAsync\(\) Method

An asynchronous version of SACommand.ExecuteReader, which Executes a SQL statement that returns a result set.



Visual Basic
:   ```
Public Shadows Function ExecuteReaderAsync () As Task< SADataReader >
```

C\#
:   ```
public new Task< SADataReader > ExecuteReaderAsync ()
```



## Returns

A task representing the asynchronous operation.



## Exceptions

SAException class
:   The database server returned an error while executing the command text.



## Remarks

Exceptions are reported via the returned Task object.

