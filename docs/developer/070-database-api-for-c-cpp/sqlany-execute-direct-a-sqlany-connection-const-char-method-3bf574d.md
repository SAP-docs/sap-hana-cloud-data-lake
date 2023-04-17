<!-- loio3bf574d16c5f1014bb52fbbc60837698 -->

# sqlany\_execute\_direct\(a\_sqlany\_connection \*, const char \*\) Method

Executes the SQL statement specified by the string argument and possibly returns a result set.



```
public a_sqlany_stmt * sqlany_execute_direct (
    a_sqlany_connection * sqlany_conn,
    const char * sql_str
)
```



## Parameters

sqlany\_conn
:   A connection object with a connection established using sqlany\_connect\(\).

sql\_str
:   A SQL string. The SQL string should not have parameters such as ?.



## Returns

A statement handle if the function executes successfully, NULL when the function executes unsuccessfully.



## Remarks

Use this method to prepare and execute a statement, or instead of calling sqlany\_prepare\(\) followed by sqlany\_execute\(\).

The following example shows how to execute a statement that returns a result set:

```
a_sqlany_stmt *   stmt;

stmt = sqlany_execute_direct( sqlany_conn, "select * from employees" );
if( stmt && sqlany_num_cols( stmt ) > 0 ) {
   while( sqlany_fetch_next( stmt ) ) {
       int i;
           for( i = 0; i < sqlany_num_cols( stmt ); i++ ) {
           // Get column i data 
       }
   }
   sqlany_free_stmt( stmt  );
}
```

> ### Note:  
> This function cannot be used for executing a SQL statement with parameters.

**Related Information**  


[sqlany\_fetch\_absolute\(a\_sqlany\_stmt \*, sacapi\_i32\) Method](sqlany-fetch-absolute-a-sqlany-stmt-sacapi-i32-method-3bf5955.md "Moves the current row in the result set to the specified row number and then fetches rows of data starting from the current row.")

[sqlany\_fetch\_next\(a\_sqlany\_stmt \*\) Method](sqlany-fetch-next-a-sqlany-stmt-method-3bf59e2.md "Returns the next set of rows from the result set.")

[sqlany\_num\_cols\(a\_sqlany\_stmt \*\) Method](sqlany-num-cols-a-sqlany-stmt-method-3bf6809.md "Returns number of columns in the result set.")

[sqlany\_get\_column\(a\_sqlany\_stmt \*, sacapi\_u32, a\_sqlany\_data\_value \*\) Method](sqlany-get-column-a-sqlany-stmt-sacapi-u32-a-sqlany-data-value-method-3bf61bb.md "Fills the supplied buffer with the value fetched for the specified column at the current row.")

