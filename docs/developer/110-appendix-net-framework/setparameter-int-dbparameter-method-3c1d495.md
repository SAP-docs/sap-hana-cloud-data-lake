<!-- loio3c1d49536c5f101489afd01b419d92f3 -->

# SetParameter\(int, DbParameter\) Method

Sets a parameter in the SAParameterCollection object.



Visual Basic
:   ```
Protected Overrides Sub SetParameter (
    ByVal index As Integer,
    ByVal value As DbParameter
)
```

C\#
:   ```
protected override void SetParameter (
    int index,
    DbParameter value
)
```



## Parameters

index
:   The zero-based index of the parameter to set.

value
:   A System.Data.Common.DbParameter to be inserted into the SAParameterCollection object.

**Related Information**  


[SAParameterCollection Class](saparametercollection-class-3c1d81e.md "Represents all parameters to an SACommand object and, optionally, their mapping to a DataSet column.")

