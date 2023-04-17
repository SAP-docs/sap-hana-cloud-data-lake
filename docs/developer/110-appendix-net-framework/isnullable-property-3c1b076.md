<!-- loio3c1b07666c5f1014a3e5ee18d6b203ce -->

# IsNullable Property

Gets and sets a value indicating whether the parameter accepts null values.



Visual Basic
:   ```
Public Overrides Property IsNullable As Boolean
```

C\#
:   ```
public override bool IsNullable {get;set;}
```



## Remarks

This property is true if null values are accepted; otherwise, it is false. The default is false. Null values are handled using the DBNull class.

