<!-- loio3bdf544f6c5f1014b752f2e1c0142d1c -->

# sasql\_fetch\_object

Fetches one row from the result set as an object.



```
object sasql_fetch_object( sasql_result <$result> )
```



## Parameters

$result
:   The result resource returned by the sasql\_query function.



## Returns

An object representing the fetched row in the result set where each property name matches one of the result set column names, or FALSE if there are no more rows in result set.

