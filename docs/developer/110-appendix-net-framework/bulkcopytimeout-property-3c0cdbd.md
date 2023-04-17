<!-- loio3c0cdbd16c5f1014830ebad371dc7ab1 -->

# BulkCopyTimeout Property

Gets or sets the number of seconds for the operation to complete before it times out.



Visual Basic
:   ```
Public Property BulkCopyTimeout As Integer
```

C\#
:   ```
public int BulkCopyTimeout {get;set;}
```



## Remarks

The default value is 30 seconds.

A value of zero indicates no limit. This value should be avoided because it may cause an indefinite wait.

If the operation times out, then all rows in the current transaction are rolled back and an SAException is raised.

Setting this property to a value less than zero is an error.

