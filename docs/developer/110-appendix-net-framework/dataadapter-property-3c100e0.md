<!-- loio3c100e096c5f1014aeb5a75deafd7881 -->

# DataAdapter Property

Specifies the SADataAdapter for which to generate statements.



Visual Basic
:   ```
Public Shadows Property DataAdapter As SADataAdapter
```

C\#
:   ```
public new SADataAdapter DataAdapter {get;set;}
```



## Remarks

An SADataAdapter object.

When you create a new instance of SACommandBuilder, any existing SACommandBuilder that is associated with this SADataAdapter is released.

