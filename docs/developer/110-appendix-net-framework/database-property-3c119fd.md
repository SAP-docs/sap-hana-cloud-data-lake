<!-- loio3c119fda6c5f1014b01dfce0828d417d -->

# Database Property

Gets the name of the current database.



Visual Basic
:   ```
Public ReadOnly Overrides Property Database As String
```

C\#
:   ```
public override string Database {get;}
```



## Remarks

If the connection is open, then the SAConnection object returns the name of the current database. Otherwise, SAConnection looks in the connection string in the following order: DatabaseName, DBN, DataSourceName, Data Source, DSN, DatabaseFile, DBF, FileDataSourceName, FileDSN.

