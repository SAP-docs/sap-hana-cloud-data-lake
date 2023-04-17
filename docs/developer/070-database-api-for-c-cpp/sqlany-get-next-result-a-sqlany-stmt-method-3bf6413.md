<!-- loio3bf641336c5f10148dc7d998891c353b -->

# sqlany\_get\_next\_result\(a\_sqlany\_stmt \*\) Method

Advances to the next result set in a multiple result set query.



```
public sacapi_bool sqlany_get_next_result (a_sqlany_stmt * sqlany_stmt)
```



## Parameters

sqlany\_stmt
:   A statement object executed by sqlany\_execute\(\) or sqlany\_execute\_direct\(\).



## Returns

1 if the statement successfully advances to the next result set, 0 otherwise.



## Remarks

If a query \(such as a call to a stored procedure\) returns multiple result sets, then this function advances from the current result set to the next.

The following example demonstrates how to advance to the next result set in a multiple result set query:

```
stmt = sqlany_execute_direct( sqlany_conn, "call my_multiple_results_procedure()" );
if( result ) {
   do {
       while( sqlany_fetch_next( stmt ) ) {
          // get column data    
       }
   } while( sqlany_get_next_result( stmt ) );
   sqlany_free_stmt( stmt );
}
```

**Related Information**  


[sqlany\_execute\_direct\(a\_sqlany\_connection \*, const char \*\) Method](sqlany-execute-direct-a-sqlany-connection-const-char-method-3bf574d.md "Executes the SQL statement specified by the string argument and possibly returns a result set.")

[sqlany\_execute\(a\_sqlany\_stmt \*\) Method](sqlany-execute-a-sqlany-stmt-method-3bf58a8.md "Executes a prepared statement.")

