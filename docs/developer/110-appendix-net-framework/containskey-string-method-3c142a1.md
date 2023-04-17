<!-- loio3c142a146c5f10149540fbc2c5656735 -->

# ContainsKey\(string\) Method

Determines whether the SAConnectionStringBuilder object contains a specific keyword.



Visual Basic
:   ```
Public Overrides Function ContainsKey (ByVal keyword As String) As Boolean
```

C\#
:   ```
public override bool ContainsKey (string keyword)
```



## Parameters

keyword
:   The keyword to locate in the SAConnectionStringBuilder.



## Returns

True if the value associated with keyword has been set; false otherwise.



The following statement determines whether the SAConnectionStringBuilder object contains the UserID keyword.

```
connectString.ContainsKey("UserID")
```

