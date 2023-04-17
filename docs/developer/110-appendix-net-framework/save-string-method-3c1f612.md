<!-- loio3c1f61296c5f10149327870970938f76 -->

# Save\(string\) Method

Creates a savepoint in the transaction that can be used to roll back a portion of the transaction, and specifies the savepoint name.



Visual Basic
:   ```
Public Sub Save (ByVal savePoint As String)
```

C\#
:   ```
public unsafe void Save (string savePoint)
```



## Parameters

savePoint
:   The name of the savepoint to which to roll back.

