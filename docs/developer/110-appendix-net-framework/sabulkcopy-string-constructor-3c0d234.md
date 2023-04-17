<!-- loio3c0d234a6c5f10149fb3a20051525ef8 -->

# SABulkCopy\(string\) Constructor

Initializes an SABulkCopy object.



Visual Basic
:   ```
Public Sub SABulkCopy (ByVal connectionString As String)
```

C\#
:   ```
public SABulkCopy (string connectionString)
```



## Parameters

connectionString
:   The string defining the connection that is opened for use by the SABulkCopy instance. A connection string is a semicolon-separated list of keyword=value pairs.



## Remarks

This syntax opens a connection during WriteToServer using connectionString. The connection is closed at the end of WriteToServer.

