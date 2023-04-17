<!-- loio3c1142116c5f1014ba94ea1487e95731 -->

# BeginTransaction\(SAIsolationLevel\) Method

Returns a transaction object.



Visual Basic
:   ```
Public Function BeginTransaction (ByVal isolationLevel As SAIsolationLevel) As SATransaction
```

C\#
:   ```
public SATransaction BeginTransaction (SAIsolationLevel isolationLevel)
```



## Parameters

isolationLevel
:   A member of the SAIsolationLevel enumeration. The default value is ReadCommitted.



## Returns

An SATransaction object representing the new transaction.



## Remarks

Commands associated with a transaction object are executed as a single transaction. The transaction is terminated with a call to the Commit or Rollback methods.

To associate a command with a transaction object, use the SACommand.Transaction property.

For more information, see "Transaction processing".

For more information, see "Typical types of inconsistency".

**Related Information**  


[SATransaction Class](satransaction-class-3c1f791.md "Represents a SQL transaction.")

[Transaction Property](transaction-property-3c0fe5b.md "Specifies the SATransaction object in which the SACommand executes.")

[SAIsolationLevel Enumeration](saisolationlevel-enumeration-3c1f80b.md "Specifies database server isolation levels.")

[Commit\(\) Method](commit-method-3c1eff8.md "Commits the database transaction.")

[Rollback\(\) Method](rollback-method-3c1f40f.md "Rolls back a transaction from a pending state.")

[Rollback\(string\) Method](rollback-string-method-3c1f48c.md "Rolls back a transaction from a pending state.")

