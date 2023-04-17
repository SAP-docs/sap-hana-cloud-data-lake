<!-- loio3c15a5ea6c5f10149355ed7870791f5e -->

# SADataAdapter\(string, SAConnection\) Constructor

Initializes an SADataAdapter object with the specified SELECT statement and connection.



Visual Basic
:   ```
Public Sub SADataAdapter (
    ByVal selectCommandText As String,
    ByVal selectConnection As SAConnection
)
```

C\#
:   ```
public SADataAdapter (
    string selectCommandText,
    SAConnection selectConnection
)
```



## Parameters

selectCommandText
:   A SELECT statement to be used to set the SADataAdapter.SelectCommand property of the SADataAdapter object.

selectConnection
:   An SAConnection object that defines a connection to a database.

**Related Information**  


[SADataAdapter\(\) Constructor](sadataadapter-constructor-3c15908.md "Initializes an SADataAdapter object.")

[SADataAdapter\(SACommand\) Constructor](sadataadapter-sacommand-constructor-3c159b7.md "Initializes an SADataAdapter object with the specified SELECT statement.")

[SADataAdapter\(string, string\) Constructor](sadataadapter-string-string-constructor-3c15ae7.md "Initializes an SADataAdapter object with the specified SELECT statement and connection string.")

[SelectCommand Property](selectcommand-property-3c15c40.md "Specifies an SACommand that is used during Fill or FillSchema to obtain a result set from the database for copying into a DataSet.")

[SAConnection Class](saconnection-class-3c126bb.md "Represents a connection to a database.")

