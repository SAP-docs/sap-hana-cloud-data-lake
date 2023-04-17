<!-- loio3c10c45b6c5f1014bb66c84d62433040 -->

# UnquoteIdentifier\(string\) Method

Returns the correct unquoted form of a quoted identifier, including properly un-escaping any embedded quotes in the identifier.



Visual Basic
:   ```
Public Overrides Function UnquoteIdentifier (ByVal quotedIdentifier As String) As String
```

C\#
:   ```
public override string UnquoteIdentifier (string quotedIdentifier)
```



## Parameters

quotedIdentifier
:   The string representing the quoted identifier that will have its embedded quotes removed.



## Returns

Returns a string representing the unquoted form of a quoted identifier with embedded quotes properly un-escaped.

