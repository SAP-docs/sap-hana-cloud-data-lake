<!-- loio3c174a026c5f101494bb85c962e4f2de -->

# RecordsAffected Property

The number of rows changed, inserted, or deleted by the execution of the SQL statement.



Visual Basic
:   ```
Public ReadOnly Overrides Property RecordsAffected As Integer
```

C\#
:   ```
public override int RecordsAffected {get;}
```



## Remarks

The number of rows changed, inserted, or deleted. This value is 0 if no rows were affected or the statement failed, and -1 for SELECT statements.

The value of this property is cumulative. For example, if two records are inserted in batch mode, then the value of RecordsAffected is 2.

IsClosed and RecordsAffected are the only properties that you can use after the SADataReader is closed.

