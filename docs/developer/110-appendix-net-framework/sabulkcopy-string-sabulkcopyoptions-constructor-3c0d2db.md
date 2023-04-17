<!-- loio3c0d2dbe6c5f1014b436a84c625f7735 -->

# SABulkCopy\(string, SABulkCopyOptions\) Constructor

Initializes an SABulkCopy object.



Visual Basic
:   ```
Public Sub SABulkCopy (
    ByVal connectionString As String,
    ByVal copyOptions As SABulkCopyOptions
)
```

C\#
:   ```
public SABulkCopy (
    string connectionString,
    SABulkCopyOptions copyOptions
)
```



## Parameters

connectionString
:   The string defining the connection that is opened for use by the SABulkCopy instance. A connection string is a semicolon-separated list of keyword=value pairs.

copyOptions
:   A combination of values from the SABulkCopyOptions enumeration that determines which data source rows are copied to the destination table.



## Remarks

This syntax opens a connection during WriteToServer using connectionString. The connection is closed at the end of WriteToServer. The copyOptions parameter has the effects described above.

