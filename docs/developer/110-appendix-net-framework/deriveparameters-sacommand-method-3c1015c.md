<!-- loio3c1015cb6c5f10148f0b95fd640298a4 -->

# DeriveParameters\(SACommand\) Method

Populates the Parameters collection of the specified SACommand object.



Visual Basic
:   ```
Public Shared Sub DeriveParameters (ByVal command As SACommand)
```

C\#
:   ```
public static void DeriveParameters (SACommand command)
```



## Parameters

command
:   An SACommand object for which to derive parameters.



## Remarks

This method is used for the stored procedure specified in the SACommand.

DeriveParameters overwrites any existing parameter information for the SACommand.

DeriveParameters requires an extra call to the database server. If the parameter information is known in advance, then it is more efficient to populate the Parameters collection by setting the information explicitly.

