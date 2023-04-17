<!-- loio3c0fe5b16c5f1014a6078a952bfe5379 -->

# Transaction Property

Specifies the SATransaction object in which the SACommand executes.



Visual Basic
:   ```
Public Shadows Property Transaction As SATransaction
```

C\#
:   ```
public new SATransaction Transaction {get;set;}
```



## Remarks

The default value is a null reference. In Visual Basic, this is Nothing.

You cannot set the Transaction property if it is already set to a specific value and the command is executing. If you set the transaction property to an SATransaction object that is not connected to the same SAConnection object as the SACommand object, then an exception is thrown the next time you attempt to execute a statement.

For more information, see "Transaction processing".

**Related Information**  


[SATransaction Class](satransaction-class-3c1f791.md "Represents a SQL transaction.")

