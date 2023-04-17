<!-- loio3c14b0496c5f1014ba5e8d3f6b096db7 -->

# this\[string keyword\] Property

Gets or sets the value of the connection keyword.



Visual Basic
:   ```
Public Overrides Property Item (ByVal keyword As String) As Object
```

C\#
:   ```
public override object this[string keyword] {get;set;}
```



## Remarks

An object representing the value of the specified connection keyword.

If the keyword or type is invalid, then an exception is raised. The parameter value is case insensitive.

When setting the value, passing NULL clears the value.

