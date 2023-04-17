<!-- loio3c15ae7e6c5f10149a5d9df73774bc6a -->

# SADataAdapter\(string, string\) Constructor

Initializes an SADataAdapter object with the specified SELECT statement and connection string.



Visual Basic
:   ```
Public Sub SADataAdapter (
    ByVal selectCommandText As String,
    ByVal selectConnectionString As String
)
```

C\#
:   ```
public SADataAdapter (
    string selectCommandText,
    string selectConnectionString
)
```



## Parameters

selectCommandText
:   A SELECT statement to be used to set the SADataAdapter.SelectCommand property of the SADataAdapter object.

selectConnectionString
:   A connection string for a database.

**Related Information**  


[SADataAdapter\(\) Constructor](sadataadapter-constructor-3c15908.md "Initializes an SADataAdapter object.")

[SADataAdapter\(SACommand\) Constructor](sadataadapter-sacommand-constructor-3c159b7.md "Initializes an SADataAdapter object with the specified SELECT statement.")

[SADataAdapter\(string, SAConnection\) Constructor](sadataadapter-string-saconnection-constructor-3c15a5e.md "Initializes an SADataAdapter object with the specified SELECT statement and connection.")

[SelectCommand Property](selectcommand-property-3c15c40.md "Specifies an SACommand that is used during Fill or FillSchema to obtain a result set from the database for copying into a DataSet.")

