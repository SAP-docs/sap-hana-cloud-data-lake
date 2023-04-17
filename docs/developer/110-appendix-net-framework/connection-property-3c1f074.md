<!-- loio3c1f07496c5f1014bf35f261cb303df1 -->

# Connection Property

The SAConnection object associated with the transaction, or a null reference \(Nothing in Visual Basic\) if the transaction is no longer valid.



Visual Basic
:   ```
Public ReadOnly Shadows Property Connection As SAConnection
```

C\#
:   ```
public new SAConnection Connection {get;}
```



## Remarks

A single application can have multiple database connections, each with zero or more transactions. This property enables you to determine the connection object associated with a particular transaction created by BeginTransaction.

