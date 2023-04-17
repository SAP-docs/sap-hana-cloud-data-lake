<!-- loio3c1c17206c5f101482b2a1a755ea6742 -->

# Add\(string, SADbType\) Method

Adds an SAParameter object to this collection, created using the specified parameter name and data type, to the collection.



Visual Basic
:   ```
Public Function Add (
    ByVal parameterName As String,
    ByVal saDbType As SADbType
) As SAParameter
```

C\#
:   ```
public SAParameter Add (
    string parameterName,
    SADbType saDbType
)
```



## Parameters

parameterName
:   The name of the parameter.

saDbType
:   One of the SADbType values.



## Returns

The new SAParameter object.

**Related Information**  


[SADbType Enumeration](sadbtype-enumeration-3c0cc44.md "Enumerates the database server .NET database data types.")

[Add\(SAParameter\) Method](add-saparameter-method-3c1c081.md "Adds an SAParameter object to this collection.")

[Add\(string, object\) Method](add-string-object-method-3c1c2d9.md "Adds an SAParameter object to this collection, created using the specified parameter name and value, to the collection.")

