<!-- loio81e312196ce21014aafac9ae60f87d1d -->

# SACredential\(string, SecureString\) Constructor

Initializes an SACredential object.



Visual Basic
:   ```
Public Sub SACredential (
    ByVal userId As String,
    ByVal password As SecureString
)
```

C\#
:   ```
public SACredential (
    string userId,
    SecureString password
)
```



## Parameters

userId
:   The user ID.

password
:   The password; a System.Security.SecureString value marked as read-only. Passing a read/write System.Security.SecureString parameter will raise an System.ArgumentException.

**Related Information**  


[SAConnection Class](saconnection-class-3c126bb.md "Represents a connection to a database.")

