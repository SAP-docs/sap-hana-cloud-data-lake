<!-- loio3bdf98836c5f1014832387b105888a27 -->

# sasql\_multi\_query

Prepares and executes one or more SQL queries.



```
bool sasql_multi_query( sasql_conn <$conn>, string <$sql_str> )
```



## Parameters

$conn
:   The connection resource returned by a connect function.

$sql\_str
:   One or more SQL statements separated by semicolons.



## Returns

TRUE on success or FALSE on failure.



## Remarks

Prepares and executes one or more SQL queries specified by *<$sql\_str\>* using the supplied connection resource. Each query is separated from the other using semicolons.

The first query result can be retrieved or stored using sasql\_use\_result or sasql\_store\_result. sasql\_field\_count can be used to check if the query returns a result set or not.

All subsequent query results can be processed using sasql\_next\_result and sasql\_use\_result/sasql\_store\_result.

