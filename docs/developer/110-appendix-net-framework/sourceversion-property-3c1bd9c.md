<!-- loio3c1bd9c76c5f1014a356a4cd2b664d5b -->

# SourceVersion Property

Gets and sets the DataRowVersion to use when loading Value.



Visual Basic
:   ```
Public Overrides Property SourceVersion As DataRowVersion
```

C\#
:   ```
public override DataRowVersion SourceVersion {get;set;}
```



## Remarks

Used by UpdateCommand during an Update operation to determine whether the parameter value is set to Current or Original. This property allows primary keys to be updated. This property is ignored by InsertCommand and DeleteCommand. This property is set to the version of the DataRow used by the Item property, or the GetChildRows method of the DataRow object.

