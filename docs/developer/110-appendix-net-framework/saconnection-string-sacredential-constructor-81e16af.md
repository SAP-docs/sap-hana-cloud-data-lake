<!-- loio81e16afd6ce210149c7f9379856d5615 -->

# SAConnection\(string, SACredential\) Constructor

Initializes a new instance of the SAConnection class given a connection string, and a SACredential object that contains the user ID and password.



Visual Basic
:   ```
Public Sub SAConnection (
    ByVal connectionString As String,
    ByVal credential As SACredential
)
```

C\#
:   ```
public SAConnection (
    string connectionString,
    SACredential credential
)
```



## Parameters

connectionString
:   A connection string. A connection string is a semicolon-separated list of keyword=value pairs. For a list of connection parameters, see "Connection parameters".

credential
:   A SACredential object. If credential is null, then SAConnection\(String, SACredential\) is functionally equivalent to SAConnection\(String\).

**Related Information**  


[SAConnection Class](saconnection-class-3c126bb.md "Represents a connection to a database.")

