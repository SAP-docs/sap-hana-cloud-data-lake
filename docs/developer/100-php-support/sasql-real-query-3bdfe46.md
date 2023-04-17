<!-- loio3bdfe4616c5f1014bdbab7480c3b9dab -->

# sasql\_real\_query

Executes a query against the database using the supplied connection resource.



```
bool sasql_real_query( sasql_conn <$conn>, string <$sql_str> )
```



## Parameters

$conn
:   The connection resource returned by a connect function.

$sql\_str
:   A SQL statement supported by the database server.



## Returns

TRUE on success or FALSE on failure.



## Remarks

The query result can be retrieved or stored using sasql\_store\_result or sasql\_use\_result. The sasql\_field\_count function can be used to check if the query returns a result set or not.

The sasql\_query function is equivalent to calling this function and one of sasql\_store\_result or sasql\_use\_result.

