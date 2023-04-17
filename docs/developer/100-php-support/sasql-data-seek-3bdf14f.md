<!-- loio3bdf14f86c5f10149d24aa0dfde86852 -->

# sasql\_data\_seek

Positions the cursor on row.



```
bool sasql_data_seek( sasql_result <$result>, int <row_num> )
```



## Parameters

$result
:   The result resource returned by the sasql\_query function.

row\_num
:   An integer that represents the new position of the cursor within the result resource. For example, specify 0 to move the cursor to the first row of the result set or 5 to move it to the sixth row. Negative numbers represent rows relative to the end of the result set. For example, -1 moves the cursor to the last row in the result set and -2 moves it to the second-last row.



## Returns

TRUE on success or FALSE on error.



## Remarks

Positions the cursor on row *<row\_num\>* on the *<$result\>* that was opened using sasql\_query.

