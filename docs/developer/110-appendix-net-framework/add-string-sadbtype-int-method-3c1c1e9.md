<!-- loio3c1c1e9b6c5f10148265a2d5a7ba968e -->

# Add\(string, SADbType, int\) Method

Adds an SAParameter object to this collection, created using the specified parameter name, data type, and length, to the collection.



Visual Basic
:   ```
Public Function Add (
    ByVal parameterName As String,
    ByVal saDbType As SADbType,
    ByVal size As Integer
) As SAParameter
```

C\#
:   ```
public SAParameter Add (
    string parameterName,
    SADbType saDbType,
    int size
)
```



## Parameters

parameterName
:   The name of the parameter.

saDbType
:   One of the SADbType values.

size
:   The length of the parameter.



## Returns

The new SAParameter object.

**Related Information**  


[SADbType Enumeration](sadbtype-enumeration-3c0cc44.md "Enumerates the database server .NET database data types.")

[Add\(SAParameter\) Method](add-saparameter-method-3c1c081.md "Adds an SAParameter object to this collection.")

[Add\(string, object\) Method](add-string-object-method-3c1c2d9.md "Adds an SAParameter object to this collection, created using the specified parameter name and value, to the collection.")

