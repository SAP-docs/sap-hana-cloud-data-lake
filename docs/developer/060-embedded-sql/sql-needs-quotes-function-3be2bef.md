<!-- loio3be2bef56c5f1014a2d3c6a3903659dc -->

# sql\_needs\_quotes Function

Determine if quotes are needed for a SQL identifier.



```
unsigned int sql_needs_quotes( SQLCA *<sqlca>, char * <str> );
```



## Parameters

sqlca
:   A pointer to a SQLCA structure.

str
:   A string of characters that is a candidate for a SQL identifier.



## Returns

TRUE or FALSE indicating whether the string requires double quotes around it when it is used as a SQL identifier.



## Remarks

This function formulates a request to the database server to determine if quotes are needed. Relevant information is stored in the sqlcode field.

There are three cases of return value/code combinations:

return = FALSE, sqlcode = 0
:   The string does not need quotes.

return = TRUE
:   The sqlcode is always SQLE\_WARNING, and the string requires quotes.

return = FALSE
:   If sqlcode is something other than 0 or SQLE\_WARNING, the test is inconclusive.

