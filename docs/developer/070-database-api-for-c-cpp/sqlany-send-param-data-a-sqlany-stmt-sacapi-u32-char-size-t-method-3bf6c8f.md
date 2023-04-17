<!-- loio3bf6c8fc6c5f1014810aed26169ab484 -->

# sqlany\_send\_param\_data\(a\_sqlany\_stmt \*, sacapi\_u32, char \*, size\_t\) Method

Sends data as part of a bound parameter.



```
public sacapi_bool sqlany_send_param_data (
    a_sqlany_stmt * sqlany_stmt,
    sacapi_u32 index,
    char * buffer,
    size_t size
)
```



## Parameters

sqlany\_stmt
:   A statement prepared successfully using sqlany\_prepare\(\).

index
:   The index of the parameter. This should be a number between 0 and sqlany\_num\_params\(\) - 1.

buffer
:   The data to be sent.

size
:   The number of bytes to send.



## Returns

1 on success or 0 on failure.



## Remarks

This method can be used to send a large amount of data for a bound parameter in chunks. This method can be used only when the batch size is 1.

**Related Information**  


[sqlany\_prepare\(a\_sqlany\_connection \*, const char \*\) Method](sqlany-prepare-a-sqlany-connection-const-char-method-3bf6a1b.md "Prepares a supplied SQL string.")

