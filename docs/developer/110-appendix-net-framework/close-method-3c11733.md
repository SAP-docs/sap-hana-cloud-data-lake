<!-- loio3c11733e6c5f10149701da29891add5e -->

# Close\(\) Method

Closes a database connection.



Visual Basic
:   ```
Public Overrides Sub Close ()
```

C\#
:   ```
public override void Close ()
```



## Remarks

The Close method rolls back any pending transactions. It then releases the connection to the connection pool, or closes the connection if connection pooling is disabled. If Close is called while handling a StateChange event, then no additional StateChange events are fired. An application can call Close multiple times.

