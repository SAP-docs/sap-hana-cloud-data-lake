<!-- loio3c0fed9b6c5f1014af54e50c080156c2 -->

# UpdatedRowSource Property

Gets or sets how command results are applied to the DataRow when used by the Update method of the SADataAdapter.



Visual Basic
:   ```
Public Overrides Property UpdatedRowSource As UpdateRowSource
```

C\#
:   ```
public override UpdateRowSource UpdatedRowSource {get;set;}
```



## Remarks

One of the UpdatedRowSource values. The default value is UpdateRowSource.OutputParameters. If the command is automatically generated, then this property is UpdateRowSource.None.

UpdatedRowSource.Both, which returns both resultset and output parameters, is not supported.

