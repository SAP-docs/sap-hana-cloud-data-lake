<!-- loio3bf6493d6c5f10149ffdd55876248c31 -->

# sqlany\_init\_ex\(const char \*, sacapi\_u32, sacapi\_u32 \*\) Method

Initializes the interface using a context.



```
public a_sqlany_interface_context * sqlany_init_ex (
    const char * app_name,
    sacapi_u32 api_version,
    sacapi_u32 * version_available
)
```



## Parameters

app\_name
:   A string that names the API used, for example "PHP", "PERL", or "RUBY".

api\_version
:   The current API version that the application is using. This should normally be one of the SQLANY\_API\_VERSION\_\* macros

version\_available
:   An optional argument to return the maximum API version that is supported.



## Returns

a context object on success and NULL on failure.

**Related Information**  


[sqlany\_fini\_ex\(a\_sqlany\_interface\_context \*\) Method](sqlany-fini-ex-a-sqlany-interface-context-method-3bf5a63.md "Finalize the interface that was created using the specified context.")

