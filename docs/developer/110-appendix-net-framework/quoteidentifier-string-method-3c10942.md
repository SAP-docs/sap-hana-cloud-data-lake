<!-- loio3c1094206c5f1014aca99548cf091e80 -->

# QuoteIdentifier\(string\) Method

Returns the correct quoted form of an unquoted identifier, including properly escaping any embedded quotes in the identifier.



Visual Basic
:   ```
Public Overrides Function QuoteIdentifier (ByVal unquotedIdentifier As String) As String
```

C\#
:   ```
public override string QuoteIdentifier (string unquotedIdentifier)
```



## Parameters

unquotedIdentifier
:   The string representing the unquoted identifier that will have to be quoted.



## Returns

Returns a string representing the quoted form of an unquoted identifier with embedded quotes properly escaped.

