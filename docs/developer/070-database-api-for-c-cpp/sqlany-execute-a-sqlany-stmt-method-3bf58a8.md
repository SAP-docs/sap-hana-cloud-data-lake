<!-- loio3bf58a8b6c5f101492becd0c6dedf44f -->

# sqlany\_execute\(a\_sqlany\_stmt \*\) Method

Executes a prepared statement.



```
public sacapi_bool sqlany_execute (a_sqlany_stmt * sqlany_stmt)
```



## Parameters

sqlany\_stmt
:   A statement prepared successfully using sqlany\_prepare\(\).



## Returns

1 if the statement is executed successfully or 0 on failure.



## Remarks

You can use sqlany\_num\_cols\(\) to verify if the executed statement returned a result set.

The following example shows how to execute a statement that does not return a result set:

```
a_sqlany_stmt *          stmt;
int                      i;
a_sqlany_bind_param   param;

stmt = sqlany_prepare( sqlany_conn, "insert into moe(id,value) values( ?,? )" );
if( stmt ) {
   sqlany_describe_bind_param( stmt, 0, &param );
   param.value.buffer = (char *)&i;
   param.value.type   = A_VAL32;
   sqlany_bind_param( stmt, 0, &param );

   sqlany_describe_bind_param( stmt, 1, &param );
   param.value.buffer = (char *)&i;
   param.value.type   = A_VAL32;
   sqlany_bind_param( stmt, 1, &param );

   for( i = 0; i < 10; i++ ) {
       if( !sqlany_execute( stmt ) ) { 
               // call sqlany_error()
           }
   }
   sqlany_free_stmt( stmt );
}
```

**Related Information**  


[sqlany\_prepare\(a\_sqlany\_connection \*, const char \*\) Method](sqlany-prepare-a-sqlany-connection-const-char-method-3bf6a1b.md "Prepares a supplied SQL string.")

