<!-- loio3c115a746c5f101496c4ee7439b3a20e -->

# ChangePassword\(string, string\) Method

Changes the password to the supplied new password for the user indicated in the connection string.



Visual Basic
:   ```
Public Shared Sub ChangePassword (
    ByVal connectionString As String,
    ByVal newPassword As String
)
```

C\#
:   ```
public static void ChangePassword (
    string connectionString,
    string newPassword
)
```



## Parameters

connectionString
:   The connection string that contains enough information to connect to the database server that you want. The connection string may contain the user ID and the current password.

newPassword
:   The new password to set. This password must comply with any password security policy set on the database server, including minimum length, requirements for specific characters, and so on.



## Exceptions

ArgumentNullException
:   Either the connectionString or the newPassword parameter is null.

ArgumentException
:   The connection string includes the option to use integrated security.

