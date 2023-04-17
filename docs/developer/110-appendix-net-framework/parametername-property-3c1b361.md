<!-- loio3c1b361e6c5f10148fa5fea7cec41335 -->

# ParameterName Property

Gets and sets the name of the SAParameter.



Visual Basic
:   ```
Public Overrides Property ParameterName As String
```

C\#
:   ```
public override string ParameterName {get;set;}
```



## Remarks

The default is an empty string.



The parameter name is "param" in the following example.

```
SELECT * FROM Customers WHERE ID = :param
```

