<!-- loio3c0cf31a6c5f1014a175ccfb7307b344 -->

# DestinationTableName Property

Gets or sets the name of the destination table on the database server.



Visual Basic
:   ```
Public Property DestinationTableName As String
```

C\#
:   ```
public string DestinationTableName {get;set;}
```



## Remarks

The default value is a null reference. In Visual Basic it is Nothing.

If the value is changed while WriteToServer is executing, then the change has no effect.

If the value has not been set before a call to WriteToServer, then an InvalidOperationException is raised.

It is an error to set the value to NULL or the empty string.

