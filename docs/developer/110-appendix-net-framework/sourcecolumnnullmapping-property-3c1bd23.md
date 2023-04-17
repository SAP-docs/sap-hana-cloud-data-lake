<!-- loio3c1bd23d6c5f1014905af39d2a1cc46d -->

# SourceColumnNullMapping Property

Gets and sets value that indicates whether the source column is nullable.



Visual Basic
:   ```
Public Overrides Property SourceColumnNullMapping As Boolean
```

C\#
:   ```
public override bool SourceColumnNullMapping {get;set;}
```



## Remarks

This property allows SACommandBuilder to generate Update statements for nullable columns correctly.

If the source column is nullable, then true is returned; otherwise, false is returned.

