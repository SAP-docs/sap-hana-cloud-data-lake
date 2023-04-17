<!-- loio3c0d1b376c5f10149ec5a0d29fd4d7e3 -->

# SABulkCopy\(SAConnection, SABulkCopyOptions, SATransaction\) Constructor

Initializes an SABulkCopy object.



Visual Basic
:   ```
Public Sub SABulkCopy (
    ByVal connection As SAConnection,
    ByVal copyOptions As SABulkCopyOptions,
    ByVal externalTransaction As SATransaction
)
```

C\#
:   ```
public SABulkCopy (
    SAConnection connection,
    SABulkCopyOptions copyOptions,
    SATransaction externalTransaction
)
```



## Parameters

connection
:   An SAConnection object that is used to perform the bulk-copy operation. If the connection is not open, then an exception is thrown in WriteToServer.

copyOptions
:   A combination of values from the SABulkCopyOptions enumeration that determines which data source rows are copied to the destination table.

externalTransaction
:   An existing SATransaction instance under which the bulk copy will occur. If externalTransaction is not NULL, then the bulk-copy operation is done within it. It is an error to specify both an external transaction and the UseInternalTransaction option.

