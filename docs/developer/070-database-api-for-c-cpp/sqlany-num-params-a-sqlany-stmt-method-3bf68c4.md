<!-- loio3bf68c4c6c5f1014b13eac83fa76617c -->

# sqlany\_num\_params\(a\_sqlany\_stmt \*\) Method

Returns the number of parameters expected for a prepared statement.



```
public sacapi_i32 sqlany_num_params (a_sqlany_stmt * sqlany_stmt)
```



## Parameters

sqlany\_stmt
:   A statement object returned by the successful execution of sqlany\_prepare\(\).



## Returns

The expected number of parameters, or -1 if the statement object is not valid.

**Related Information**  


[sqlany\_prepare\(a\_sqlany\_connection \*, const char \*\) Method](sqlany-prepare-a-sqlany-connection-const-char-method-3bf6a1b.md "Prepares a supplied SQL string.")

