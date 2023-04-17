<!-- loio3bdf63c76c5f1014bfb1964cabbcb9ec -->

# sasql\_field\_count

Returns the number of columns \(fields\) the last result contains.



```
int sasql_field_count( sasql_conn <$conn> )
```



## Parameters

$conn
:   The connection resource returned by a connect function.



## Returns

A positive number of columns, or FALSE if *<$conn\>* is not valid.

