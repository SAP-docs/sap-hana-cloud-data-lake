<!-- loio3bf5802c6c5f1014baabddec3c02892f -->

# sqlany\_execute\_immediate\(a\_sqlany\_connection \*, const char \*\) Method

Executes the supplied SQL statement immediately without returning a result set.



```
public sacapi_bool sqlany_execute_immediate (
    a_sqlany_connection * sqlany_conn,
    const char * sql
)
```



## Parameters

sqlany\_conn
:   A connection object with a connection established using sqlany\_connect\(\).

sql
:   A string representing the SQL statement to be executed.



## Returns

1 on success or 0 on failure.



## Remarks

This function is useful for SQL statements that do not return a result set.

