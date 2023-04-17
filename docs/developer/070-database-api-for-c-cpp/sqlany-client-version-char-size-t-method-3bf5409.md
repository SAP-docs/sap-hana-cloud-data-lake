<!-- loio3bf540956c5f1014915ba14d1b308055 -->

# sqlany\_client\_version\(char \*, size\_t\) Method

Returns the current client version.



```
public sacapi_bool sqlany_client_version (
    char * buffer,
    size_t len
)
```



## Parameters

buffer
:   The buffer to be filled with the client version string.

len
:   The length of the buffer supplied.



## Returns

1 when successful or 0 when unsuccessful.



## Remarks

This method fills the buffer passed with the major, minor, patch, and build number of the client library. The buffer will be null-terminated.

