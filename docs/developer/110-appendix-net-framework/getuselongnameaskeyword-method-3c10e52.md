<!-- loio3c10e52a6c5f10149548c47e2a44e238 -->

# GetUseLongNameAsKeyword\(\) Method

Gets a boolean value that indicates whether long connection parameter names are used in the connection string.



Visual Basic
:   ```
Public Function GetUseLongNameAsKeyword () As Boolean
```

C\#
:   ```
public bool GetUseLongNameAsKeyword ()
```



## Returns

True if long connection parameter names are used to build connection strings; false otherwise.



## Remarks

Connection parameters have both long and short forms of their names. For example, to specify the name of an ODBC data source in your connection string, use either of the following values: DataSourceName or DSN. By default, long connection parameter names are used to build connection strings.

**Related Information**  


[SetUseLongNameAsKeyword\(bool\) Method](setuselongnameaskeyword-bool-method-3c10ecc.md "Sets a boolean value that indicates whether long connection parameter names are used in the connection string.")

