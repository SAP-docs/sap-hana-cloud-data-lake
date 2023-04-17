<!-- loio3c1b75536c5f10148a2fdb78e6447611 -->

# SAParameter\(string, SADbType, int, ParameterDirection, bool, byte, byte, string, DataRowVersion, object\) Constructor

Initializes an SAParameter object with the specified parameter name, data type, size, direction, nullability, numeric precision, numeric scale, source column, source version, and value.



Visual Basic
:   ```
Public Sub SAParameter (
    ByVal parameterName As String,
    ByVal dbType As SADbType,
    ByVal size As Integer,
    ByVal direction As ParameterDirection,
    ByVal isNullable As Boolean,
    ByVal precision As Byte,
    ByVal scale As Byte,
    ByVal sourceColumn As String,
    ByVal sourceVersion As DataRowVersion,
    ByVal value As Object
)
```

C\#
:   ```
public SAParameter (
    string parameterName,
    SADbType dbType,
    int size,
    ParameterDirection direction,
    bool isNullable,
    byte precision,
    byte scale,
    string sourceColumn,
    DataRowVersion sourceVersion,
    object value
)
```



## Parameters

parameterName
:   The name of the parameter.

dbType
:   One of the SADbType values.

size
:   The length of the parameter.

direction
:   One of the ParameterDirection values.

isNullable
:   True if the value of the field can be null; false otherwise.

precision
:   The total number of digits to the left and right of the decimal point to which Value is resolved.

scale
:   The total number of decimal places to which Value is resolved.

sourceColumn
:   The name of the source column to map.

sourceVersion
:   One of the DataRowVersion values.

value
:   An Object that is the value of the parameter.



The name of the parameter. The parameter name is "param" in the following example.

```
SELECT * FROM Customers WHERE ID = :param
```

