<!-- loio3be0d7846c5f1014b362e9ba10cf8d88 -->

# sasql\_stmt\_send\_long\_data

Allows the user to send parameter data in chunks.



```
bool sasql_stmt_send_long_data( sasql_stmt <$stmt>, int <$param_number>, string <$data> )
```



## Parameters

$stmt
:   A statement resource that was prepared using sasql\_prepare.

$param\_number
:   The parameter number. This must be a number between 0 and \(sasql\_stmt\_param\_count\($stmt\) - 1\).

$data
:   The data to be sent.



## Returns

TRUE on success or FALSE on failure.



## Remarks

The user must first call sasql\_stmt\_bind\_param or sasql\_stmt\_bind\_param\_ex before attempting to send any data. The bind parameter must be of type string or blob. Repeatedly calling this function appends on to what was previously sent.

