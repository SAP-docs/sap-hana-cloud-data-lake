<!-- loio3c1bcac36c5f1014b309a78b79014401 -->

# SourceColumn Property

Gets and sets the name of the source column mapped to the DataSet and used for loading or returning the value.



Visual Basic
:   ```
Public Overrides Property SourceColumn As String
```

C\#
:   ```
public override string SourceColumn {get;set;}
```



## Remarks

A string specifying the name of the source column mapped to the DataSet and used for loading or returning the value.

When SourceColumn is set to anything other than an empty string, the value of the parameter is retrieved from the column with the SourceColumn name. If Direction is set to Input, then the value is taken from the DataSet. If Direction is set to Output, then the value is taken from the data source. A Direction of InputOutput is a combination of both.

