<!-- loio3bf651596c5f10149db9cb34f651fe5c -->

# sqlany\_init\(const char \*, sacapi\_u32, sacapi\_u32 \*\) Method

Initializes the interface.



```
public sacapi_bool sqlany_init (
    const char * app_name,
    sacapi_u32 api_version,
    sacapi_u32 * version_available
)
```



## Parameters

app\_name
:   A string that names the application that is using the API. For example, "PHP", "PERL", or "RUBY".

api\_version
:   The version of the compiled application.

version\_available
:   An optional argument to return the maximum supported API version.



## Returns

1 on success, 0 otherwise



## Remarks

The following example demonstrates how to initialize the SQL Anywhere C API DLL:

```
sacapi_u32 api_version;
if( sqlany_init( "PHP", SQLANY_API_VERSION_1, &api_version ) ) {
   printf( "Interface initialized successfully!\n" );
} else {
   printf( "Failed to initialize the interface! Supported version=%d\n", api_version );
}
```

**Related Information**  


[sqlany\_fini\(\) Method](sqlany-fini-method-3bf5c05.md "Finalizes the interface.")

