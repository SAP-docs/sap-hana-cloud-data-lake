<!-- loio3c13e1c46c5f10148ed7be23ad3ae500 -->

# SAConnectionStringBuilder\(string\) Constructor

Initializes a new instance of the SAConnectionStringBuilder class.



Visual Basic
:   ```
Public Sub SAConnectionStringBuilder (ByVal connectionString As String)
```

C\#
:   ```
public SAConnectionStringBuilder (string connectionString)
```



## Parameters

connectionString
:   The basis for the object's internal connection information. Parsed into keyword=value pairs. For a list of connection parameters, see "Connection parameters".



The following statement initializes an SAConnection object for a connection to a database named policies running on a database server named hr. The connection uses the user ID admin and the password money.

```
SAConnectionStringBuilder conn = new SAConnectionStringBuilder(
 "UID=admin;PWD=money;SERVER=hr;DBN=policies" );
```

