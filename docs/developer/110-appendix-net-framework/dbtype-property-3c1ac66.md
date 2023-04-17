<!-- loio3c1ac6696c5f10149ab8a372ae0be0f2 -->

# DbType Property

Gets and sets the DbType of the parameter.



Visual Basic
:   ```
Public Overrides Property DbType As DbType
```

C\#
:   ```
public override DbType DbType {get;set;}
```



## Remarks

The SADbType and DbType are linked. Setting the DbType changes the SADbType to a supporting SADbType.

The value must be a member of the SADbType enumerator.

