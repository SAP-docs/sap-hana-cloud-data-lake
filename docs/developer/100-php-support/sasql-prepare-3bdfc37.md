<!-- loio3bdfc3706c5f1014b085c7120199606a -->

# sasql\_prepare

Prepares the supplied SQL string.



```
sasql_stmt sasql_prepare( sasql_conn <$conn>, string <$sql_str> )
```



## Parameters

 $conn
 :   The connection resource returned by a connect function.

  $sql\_str
 :   The SQL statement to be prepared. The string can include parameter markers by embedding question marks at the appropriate positions.

 

## Returns

A statement object or FALSE on failure. To determine the cause of failure, use the sasql\_error and sasql\_errorcode functions.

