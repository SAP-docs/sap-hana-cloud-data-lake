<!-- loio3bdf44456c5f101481589efb56c32244 -->

# sasql\_fetch\_assoc

Fetches one row from the result set as an associative array.



```
array sasql_fetch_assoc( sasql_result <$result> )
```



## Parameters

$result
:   The result resource returned by the sasql\_query function.



## Returns

An associative array of strings representing the fetched row in the result set, where each key in the array represents the name of one of the result set's columns or FALSE if there are no more rows in resultset.

