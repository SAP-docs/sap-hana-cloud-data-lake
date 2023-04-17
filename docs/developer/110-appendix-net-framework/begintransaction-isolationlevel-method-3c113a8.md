<!-- loio3c113a8f6c5f1014900dfbfe20b205e7 -->

# BeginTransaction\(IsolationLevel\) Method

Returns a transaction object.



Visual Basic
:   ```
Public Shadows Function BeginTransaction (ByVal isolationLevel As IsolationLevel) As SATransaction
```

C\#
:   ```
public new SATransaction BeginTransaction (IsolationLevel isolationLevel)
```



## Parameters

isolationLevel
:   A member of the SAIsolationLevel enumeration. The default value is ReadCommitted.



## Returns

An SATransaction object representing the new transaction.



## Remarks

Commands associated with a transaction object are executed as a single transaction. The transaction is terminated with a call to the Commit or Rollback methods.

To associate a command with a transaction object, use the SACommand.Transaction property.



```
SATransaction tx = 
 conn.BeginTransaction( SAIsolationLevel.ReadUncommitted );
```

**Related Information**  


[SATransaction Class](satransaction-class-3c1f791.md "Represents a SQL transaction.")

[Transaction Property](transaction-property-3c0fe5b.md "Specifies the SATransaction object in which the SACommand executes.")

[SAIsolationLevel Enumeration](saisolationlevel-enumeration-3c1f80b.md "Specifies database server isolation levels.")

