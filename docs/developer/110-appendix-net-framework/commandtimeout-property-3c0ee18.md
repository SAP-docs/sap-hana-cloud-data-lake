<!-- loio3c0ee18e6c5f10148c1ce122d55455bd -->

# CommandTimeout Property

This feature is not supported by the .NET Data Provider.



Visual Basic
:   ```
Public Overrides Property CommandTimeout As Integer
```

C\#
:   ```
public override int CommandTimeout {get;set;}
```



## Remarks

To set a request timeout, use the following example.

```
cmd.CommandText = "SET OPTION request_timeout = 30";
cmd.ExecuteNonQuery();
```

