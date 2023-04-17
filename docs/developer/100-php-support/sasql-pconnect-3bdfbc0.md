<!-- loio3bdfbc0b6c5f1014954cebebe64e2f23 -->

# sasql\_pconnect

Establishes a persistent connection to a database.



```
sasql_conn sasql_pconnect( string <$con_str> )
```



## Parameters

$con\_str
:   A valid connection string.



## Returns

A positively valued persistent connection resource on success, or an error and 0 on failure.



## Remarks

Because of the way Apache creates child processes, you may observe a performance gain when using sasql\_pconnect instead of sasql\_connect. Persistent connections may provide improved performance in a similar fashion to connection pooling. If your database server has a limited number of connections \(for example, the personal database server is limited to 10 concurrent connections\), caution should be exercised when using persistent connections. Persistent connections could be attached to each of the child processes, and if you have more child processes in Apache than there are available connections, you will receive connection errors.

