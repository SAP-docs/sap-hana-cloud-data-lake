<!-- loio3c117be26c5f1014a6c1ca3dc1e83446 -->

# ConnectionString Property

Provides the database connection string.



Visual Basic
:   ```
Public Overrides Property ConnectionString As String
```

C\#
:   ```
public override string ConnectionString {get;set;}
```



## Remarks

The ConnectionString is designed to match the database server connection string format as closely as possible with the following exception: when the Persist Security Info value is set to false \(the default\), the connection string that is returned is the same as the user-set ConnectionString minus security information. The .NET Data Provider does not persist the password in a returned connection string unless you set Persist Security Info to true.

Use the ConnectionString property to connect to a variety of data sources.

You can set the ConnectionString property only when the connection is closed. Many of the connection string values have corresponding read-only properties. When the connection string is set, all of these properties are updated, unless an error is detected. If an error is detected, then none of the properties are updated. SAConnection properties return only those settings contained in the ConnectionString.

If you reset the ConnectionString on a closed connection, then all connection string values and related properties are reset, including the password.

When the property is set, a preliminary validation of the connection string is performed. When an application calls the Open method, the connection string is fully validated. A runtime exception is generated if the connection string contains invalid or unsupported properties.

Values can be delimited by single or double quotes. Either single or double quotes may be used within a connection string by using the other delimiter, for example, name="value's" or name= 'value"s', but not name='value's' or name= ""value"". Blank characters are ignored unless they are placed within a value or within quotes. keyword=value pairs must be separated by a semicolon. If a semicolon is part of a value, then it must also be delimited by quotes. Escape sequences are not supported, and the value type is irrelevant. Names are not case sensitive. If a property name occurs more than once in the connection string, then the value associated with the last occurrence is used.

Use caution when constructing a connection string based on user input, such as when retrieving a user ID and password from a window, and appending it to the connection string. The application should not allow a user to embed extra connection string parameters in these values.

The default value of connection pooling is true \(pooling=true\).



The following statements set a connection string for an ODBC data source and open the connection.

```
SAConnection conn = new SAConnection();
conn.ConnectionString = "DSN=SQL Anywhere 17 Demo";
conn.Open();
```

**Related Information**  


[SAConnection Class](saconnection-class-3c126bb.md "Represents a connection to a database.")

[Open\(\) Method](open-method-3c121f1.md "Opens a database connection with the property settings specified by the SAConnection.ConnectionString.")

