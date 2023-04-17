<!-- loio3bf6131d6c5f1014aeec800b6773175b -->

# sqlany\_get\_column\_info\(a\_sqlany\_stmt \*, sacapi\_u32, a\_sqlany\_column\_info \*\) Method

Retrieves column metadata information and fills the a\_sqlany\_column\_info structure with information about the column.



```
public sacapi_bool sqlany_get_column_info (
    a_sqlany_stmt * sqlany_stmt,
    sacapi_u32 col_index,
    a_sqlany_column_info * buffer
)
```



## Parameters

sqlany\_stmt
:   A statement object created by sqlany\_prepare\(\) or sqlany\_execute\_direct\(\).

col\_index
:   The column number between 0 and sqlany\_num\_cols\(\) - 1.

buffer
:   A column info structure to be filled with column information.



## Returns

1 on success or 0 if the column index is out of range, or if the statement does not return a result set.

**Related Information**  


[sqlany\_execute\(a\_sqlany\_stmt \*\) Method](sqlany-execute-a-sqlany-stmt-method-3bf58a8.md "Executes a prepared statement.")

[sqlany\_execute\_direct\(a\_sqlany\_connection \*, const char \*\) Method](sqlany-execute-direct-a-sqlany-connection-const-char-method-3bf574d.md "Executes the SQL statement specified by the string argument and possibly returns a result set.")

[sqlany\_prepare\(a\_sqlany\_connection \*, const char \*\) Method](sqlany-prepare-a-sqlany-connection-const-char-method-3bf6a1b.md "Prepares a supplied SQL string.")

