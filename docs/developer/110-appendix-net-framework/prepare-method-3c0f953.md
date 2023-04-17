<!-- loio3c0f953b6c5f10148ff2a4a4574aae1b -->

# Prepare\(\) Method

Prepares or compiles the SACommand on the data source.



Visual Basic
:   ```
Public Overrides Sub Prepare ()
```

C\#
:   ```
public override void Prepare ()
```



## Remarks

If you call one of the ExecuteNonQuery, ExecuteReader, or ExecuteScalar methods after calling Prepare, then any parameter value that is larger than the value specified by the Size property is automatically truncated to the original specified size of the parameter, and no truncation errors are returned.

The truncation only happens for the following data types:

-   CHAR
-   VARCHAR
-   LONG VARCHAR
-   TEXT
-   NCHAR
-   NVARCHAR
-   LONG NVARCHAR
-   NTEXT
-   BINARY
-   LONG BINARY
-   VARBINARY
-   IMAGE

If the Size property is not specified, then the default value is used and the data is not truncated.

**Related Information**  


[ExecuteNonQuery\(\) Method](executenonquery-method-3c0f56f.md "Executes a statement that does not return a result set, such as an INSERT, UPDATE, DELETE, or data definition statement.")

[ExecuteReader\(\) Method](executereader-method-3c0f5ee.md "Executes a SQL statement that returns a result set.")

[ExecuteScalar\(\) Method](executescalar-method-3c0f7de.md "Executes a statement that returns a single value.")

