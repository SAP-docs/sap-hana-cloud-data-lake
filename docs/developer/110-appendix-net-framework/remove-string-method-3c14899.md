<!-- loio3c1489946c5f101480fdb5fe9d71c69b -->

# Remove\(string\) Method

Removes the entry with the specified key from the SAConnectionStringBuilder instance.



Visual Basic
:   ```
Public Overrides Function Remove (ByVal keyword As String) As Boolean
```

C\#
:   ```
public override bool Remove (string keyword)
```



## Parameters

keyword
:   The key of the key/value pair to be removed from the connection string in this SAConnectionStringBuilder.



## Returns

True if the key existed within the connection string and was removed; false if the key did not exist.

