<!-- loio3bf6a1b16c5f1014bcc1ad38c112fdb5 -->

# sqlany\_prepare\(a\_sqlany\_connection \*, const char \*\) Method

Prepares a supplied SQL string.



```
public a_sqlany_stmt * sqlany_prepare (
    a_sqlany_connection * sqlany_conn,
    const char * sql_str
)
```



## Parameters

sqlany\_conn
:   A connection object with a connection established using sqlany\_connect\(\).

sql\_str
:   The SQL statement to be prepared.



## Returns

A handle to a SQL Anywhere statement object. The statement object can be used by sqlany\_execute\(\) to execute the statement.



## Remarks

Execution does not happen until sqlany\_execute\(\) is called. The returned statement object should be freed using sqlany\_free\_stmt\(\).

The following statement demonstrates how to prepare a SELECT SQL string:

```
char * str;
a_sqlany_stmt * stmt;

str = "select * from employees where salary >= ?";
stmt = sqlany_prepare( sqlany_conn, str );
if( stmt == NULL ) {
   // Failed to prepare statement, call sqlany_error() for more info
}
```

**Related Information**  


[sqlany\_free\_stmt\(a\_sqlany\_stmt \*\) Method](sqlany-free-stmt-a-sqlany-stmt-method-3bf5db6.md "Frees resources associated with a prepared statement object.")

[sqlany\_connect\(a\_sqlany\_connection \*, const char \*\) Method](sqlany-connect-a-sqlany-connection-const-char-method-3bf5542.md "Creates a connection to a SQL Anywhere database server using the supplied connection object and connection string.")

[sqlany\_execute\(a\_sqlany\_stmt \*\) Method](sqlany-execute-a-sqlany-stmt-method-3bf58a8.md "Executes a prepared statement.")

[sqlany\_num\_params\(a\_sqlany\_stmt \*\) Method](sqlany-num-params-a-sqlany-stmt-method-3bf68c4.md "Returns the number of parameters expected for a prepared statement.")

[sqlany\_describe\_bind\_param\(a\_sqlany\_stmt \*, sacapi\_u32, a\_sqlany\_bind\_param \*\) Method](sqlany-describe-bind-param-a-sqlany-stmt-sacapi-u32-a-sqlany-bind-param-method-3bf55c0.md "Describes the bind parameters of a prepared statement.")

[sqlany\_bind\_param\(a\_sqlany\_stmt \*, sacapi\_u32, a\_sqlany\_bind\_param \*\) Method](sqlany-bind-param-a-sqlany-stmt-sacapi-u32-a-sqlany-bind-param-method-3bf5173.md "Bind a user-supplied buffer as a parameter to the prepared statement.")

