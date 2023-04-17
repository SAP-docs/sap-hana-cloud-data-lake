<!-- loio3c1f48c66c5f10148b148490aea93971 -->

# Rollback\(string\) Method

Rolls back a transaction from a pending state.



Visual Basic
:   ```
Public Sub Rollback (ByVal savePoint As String)
```

C\#
:   ```
public unsafe void Rollback (string savePoint)
```



## Parameters

savePoint
:   The name of the savepoint to roll back to.



## Remarks

The transaction can only be rolled back from a pending state \(after BeginTransaction has been called, but before Commit is called\).

