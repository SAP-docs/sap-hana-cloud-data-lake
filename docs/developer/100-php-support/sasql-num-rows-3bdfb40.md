<!-- loio3bdfb4076c5f1014bb21f4644230369d -->

# sasql\_num\_rows

Returns the number of rows in a result.



```
int sasql_num_rows( sasql_result <$result> )
```



## Parameters

$result
:   The result resource returned by the sasql\_query function.



## Returns

A positive number if the number of rows is exact, or a negative number if it is an estimate. To get the exact number of rows, the database option row\_counts must be set permanently on the database, or temporarily on the connection.



## Remarks

Returns the number of rows that the *<$result\>* contains.

