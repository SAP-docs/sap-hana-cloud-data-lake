<!-- loio3c0cac7f6c5f1014b40e9bd0a91473ed -->

# SAInfoMessageEventHandler\(object, SAInfoMessageEventArgs\) Delegate

Represents the method that handles the SAConnection.InfoMessage event of an SAConnection object.



Visual Basic
:   ```
Public Delegate Sub SAInfoMessageEventHandler (
    ByVal obj As Object,
    ByVal args As SAInfoMessageEventArgs
) As delegate void
```

C\#
:   ```
public delegate void SAInfoMessageEventHandler (
    object obj,
    SAInfoMessageEventArgs args
);
```

**Related Information**  


[SAConnection Class](saconnection-class-3c126bb.md "Represents a connection to a database.")

[InfoMessage Event](infomessage-event-3c1207c.md "Occurs when the database server returns a warning or informational message.")

