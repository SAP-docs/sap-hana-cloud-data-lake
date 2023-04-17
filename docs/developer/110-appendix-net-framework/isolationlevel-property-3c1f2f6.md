<!-- loio3c1f2f6b6c5f10148fbef95ba451bbfd -->

# IsolationLevel Property

Specifies the isolation level for this transaction.



Visual Basic
:   ```
Public ReadOnly Overrides Property IsolationLevel As System.Data.IsolationLevel
```

C\#
:   ```
public override System.Data.IsolationLevel IsolationLevel {get;}
```



## Remarks

The IsolationLevel for this transaction. This can be one of:

-   Unspecified
-   Chaos
-   ReadUncommitted
-   ReadCommitted
-   RepeatableRead
-   Serializable
-   Snapshot

The default is ReadCommitted.

