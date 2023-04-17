<!-- loio3bf538b26c5f10148b3691e7ccd9b453 -->

# sqlany\_client\_version\_ex\(a\_sqlany\_interface\_context \*, char \*, size\_t\) Method

Returns the current client version.



```
public sacapi_bool sqlany_client_version_ex (
    a_sqlany_interface_context * context,
    char * buffer,
    size_t len
)
```



## Parameters

context
:   object that was create with sqlany\_init\_ex\(\)

buffer
:   The buffer to be filled with the client version string.

len
:   The length of the buffer supplied.



## Returns

1 when successful or 0 when unsuccessful.



## Remarks

This method fills the buffer passed with the major, minor, patch, and build number of the client library. The buffer will be null-terminated.

**Related Information**  


[sqlany\_init\_ex\(const char \*, sacapi\_u32, sacapi\_u32 \*\) Method](sqlany-init-ex-const-char-sacapi-u32-sacapi-u32-method-3bf6493.md "Initializes the interface using a context.")

