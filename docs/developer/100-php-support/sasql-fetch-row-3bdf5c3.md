<!-- loio3bdf5c346c5f10148018a45c9501f2b9 -->

# sasql\_fetch\_row

Fetches one row from the result set. This row is returned as an array that can be indexed by the column indexes only.



```
array sasql_fetch_row( sasql_result <$result> )
```



## Parameters

$result
:   The result resource returned by the sasql\_query function.



## Returns

An array that represents a row from the result set, or FALSE when no rows are available.

