<!-- loio3c11328f6c5f1014816bb14615512965 -->

# BeginTransaction\(\) Method

Returns a transaction object.



Visual Basic
:   ```
Public Shadows Function BeginTransaction () As SATransaction
```

C\#
:   ```
public new SATransaction BeginTransaction ()
```



## Returns

An SATransaction object representing the new transaction.



## Remarks

Commands associated with a transaction object are executed as a single transaction. The transaction is terminated with a call to the Commit or Rollback methods.

To associate a command with a transaction object, use the SACommand.Transaction property.

**Related Information**  


[SATransaction Class](satransaction-class-3c1f791.md "Represents a SQL transaction.")

[Transaction Property](transaction-property-3c0fe5b.md "Specifies the SATransaction object in which the SACommand executes.")

