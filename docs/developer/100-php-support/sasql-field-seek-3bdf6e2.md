<!-- loio3bdf6e2d6c5f101490d4bb9704bca520 -->

# sasql\_field\_seek

Sets the field cursor to the given offset.



```
bool sasql_field_seek( sasql_result <$result>, int <$field_offset> )
```



## Parameters

$result
:   The result resource returned by the sasql\_query function.

$field\_offset
:   An integer representing the column/field on which you want to retrieve information. Columns are zero based; to get the first column, specify the value 0. If this parameter is omitted, then the next field object is returned.



## Returns

TRUE on success or FALSE on error.



## Remarks

The next call to sasql\_fetch\_field will retrieve the field definition of the column associated with that offset.

