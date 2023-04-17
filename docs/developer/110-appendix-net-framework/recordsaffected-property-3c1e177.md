<!-- loio3c1e177f6c5f1014845c83d0f2300b49 -->

# RecordsAffected Property

Returns the number of rows changed, inserted, or deleted by the execution of the SQL statement.



Visual Basic
:   ```
Public ReadOnly Shadows Property RecordsAffected As Integer
```

C\#
:   ```
public new int RecordsAffected {get;}
```



## Remarks

The number of rows changed, inserted, or deleted; 0 if no rows were affected or the statement failed; and -1 for SELECT statements.

