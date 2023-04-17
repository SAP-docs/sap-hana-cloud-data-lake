<!-- loio3c1d51116c5f10148c6cf6dd4bd4fb3c -->

# SetParameter\(string, DbParameter\) Method

Sets a parameter in the SAParameterCollection object.



Visual Basic
:   ```
Protected Overrides Sub SetParameter (
    ByVal parameterName As String,
    ByVal value As DbParameter
)
```

C\#
:   ```
protected override void SetParameter (
    string parameterName,
    DbParameter value
)
```



## Parameters

parameterName
:   The name of the parameter to set.

value
:   A System.Data.Common.DbParameter to be inserted into the SAParameterCollection object.

**Related Information**  


[SAParameterCollection Class](saparametercollection-class-3c1d81e.md "Represents all parameters to an SACommand object and, optionally, their mapping to a DataSet column.")

