<!-- loio3bdfcb3b6c5f1014b61b973fccbb355f -->

# sasql\_query

Prepares and executes a SQL query.



```
mixed sasql_query( sasql_conn <$conn>, string <$sql_str> [, int <$result_mode> ] )
```



## Parameters

 $conn
 :   The connection resource returned by a connect function.

  $sql\_str
 :   A SQL statement supported by the database server.

  $result\_mode
 :   Either SASQL\_USE\_RESULT, or SASQL\_STORE\_RESULT \(the default\).

 

## Returns

FALSE on failure; TRUE on success for INSERT, UPDATE, DELETE, CREATE; sasql\_result for SELECT.



## Remarks

Prepares, describes, and executes the SQL query *<$sql\_str\>* on the connection identified by *<$conn\>* that has already been opened using sasql\_connect or sasql\_pconnect.

The sasql\_query function is equivalent to calling two functions, sasql\_real\_query and one of sasql\_store\_result or sasql\_use\_result.

If a warning is generated at the prepare and describe steps, it will be overwritten if the execute succeeds. If you need to obtain any warnings from each step, then use the sasql\_prepare, sasql\_error, and sasql\_errorcode functions.

