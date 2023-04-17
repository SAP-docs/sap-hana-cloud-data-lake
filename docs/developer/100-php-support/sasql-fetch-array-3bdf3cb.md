<!-- loio3bdf3cbe6c5f1014b130e8183f9419ca -->

# sasql\_fetch\_array

Fetches one row from the result set.



```
array sasql_fetch_array( sasql_result <$result> [, int <$result_type> ])
```



## Parameters

$result
:   The result resource returned by the sasql\_query function.

$result\_type
:   This optional parameter is a constant indicating what type of array should be produced from the current row data. The possible values for this parameter are the constants SASQL\_ASSOC, SASQL\_NUM, or SASQL\_BOTH. It defaults to SASQL\_BOTH.

    By using the SASQL\_ASSOC constant, this function will behave identically to the sasql\_fetch\_assoc function, while SASQL\_NUM will behave identically to the sasql\_fetch\_row function. The final option SASQL\_BOTH will create a single array with the attributes of both.



## Returns

An array that represents a row from the result set, or FALSE when no rows are available.



## Remarks

The row is returned as an array that can be indexed by the column names or by the column indexes.

