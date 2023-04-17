<!-- loio3c11a7f86c5f10148c76c14702cdd656 -->

# DataSource Property

Gets the name of the database server.



Visual Basic
:   ```
Public ReadOnly Overrides Property DataSource As String
```

C\#
:   ```
public override string DataSource {get;}
```



## Remarks

If the connection is open, then the SAConnection object returns the ServerName server property. Otherwise, the SAConnection object looks in the connection string for the ServerName connection parameter.

**Related Information**  


[SAConnection Class](saconnection-class-3c126bb.md "Represents a connection to a database.")

