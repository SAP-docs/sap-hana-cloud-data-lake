<!-- loio3c14b80d6c5f1014bc67bc461b2ec887 -->

# TryGetValue\(string, out object\) Method

Retrieves a value corresponding to the supplied key from this SAConnectionStringBuilder.



Visual Basic
:   ```
Public Overrides Function TryGetValue (
    ByVal keyword As String,
    ByVal value As Object
) As Boolean
```

C\#
:   ```
public override bool TryGetValue (
    string keyword,
    out object value
)
```



## Parameters

keyword
:   The key of the item to retrieve.

value
:   The value corresponding to keyword.



## Returns

True if keyword was found within the connection string; false otherwise.

