<!-- loio3c1d72206c5f10148c3387b145bf5dab -->

# this\[string parameterName\] Property

Gets and sets the SAParameter object at the specified index.



Visual Basic
:   ```
Public Shadows Property Item (ByVal parameterNameAs String) As SAParameter
```

C\#
:   ```
public new SAParameter this[string parameterName] {get;set;}
```



## Returns

The SAParameter object with the specified name.



## Remarks

An SAParameter object.

In C\#, this property is the indexer for the SAParameterCollection object.

**Related Information**  


[SAParameter Class](saparameter-class-3c1c008.md "Represents a parameter to an SACommand, and optionally, its mapping to a DataSet column.")

[SAParameterCollection Class](saparametercollection-class-3c1d81e.md "Represents all parameters to an SACommand object and, optionally, their mapping to a DataSet column.")

[GetOrdinal\(string\) Method](getordinal-string-method-3c16b3a.md "Returns the column ordinal, given the column name.")

[GetValue\(int\) Method](getvalue-int-method-3c16eac.md "Returns the value of the specified column as an Object.")

[GetFieldType\(int\) Method](getfieldtype-int-method-3c16794.md "Returns the Type that is the data type of the object.")

