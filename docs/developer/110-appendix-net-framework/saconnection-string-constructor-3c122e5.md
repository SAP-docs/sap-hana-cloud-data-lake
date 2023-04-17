<!-- loio3c122e576c5f10148df48eba0dfdbb22 -->

# SAConnection\(string\) Constructor

Initializes an SAConnection object.



Visual Basic
:   ```
Public Sub SAConnection (ByVal connectionString As String)
```

C\#
:   ```
public SAConnection (string connectionString)
```



## Parameters

connectionString
:   A connection string. A connection string is a semicolon-separated list of keyword=value pairs. For a list of connection parameters, see "Connection parameters".



## Remarks

The connection must then be opened before you perform any operations against the database.



The following statement initializes an SAConnection object for a connection to a database named policies running on a database server named hr. The connection uses the user ID admin and the password money.

```
SAConnection conn = new SAConnection( 
   "UID=admin;PWD=money;SERVER=hr;DBN=policies" ); 
conn.Open();
```

**Related Information**  


[SAConnection Class](saconnection-class-3c126bb.md "Represents a connection to a database.")

