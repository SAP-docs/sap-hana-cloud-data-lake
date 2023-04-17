<!-- loio3c0f000b6c5f10149cd7dbd2b94feace -->

# CreateParameter\(\) Method

Provides an SAParameter object for supplying parameters to SACommand objects.



Visual Basic
:   ```
Public Shadows Function CreateParameter () As SAParameter
```

C\#
:   ```
public new SAParameter CreateParameter ()
```



## Returns

A new parameter, as an SAParameter object.



## Remarks

Stored procedures and some other SQL statements can take parameters, indicated in the text of a statement by a question mark \(?\).

The CreateParameter method provides an SAParameter object. Set properties on the SAParameter object to specify the value, data type, and so on for the parameter.

**Related Information**  


[SAParameter Class](saparameter-class-3c1c008.md "Represents a parameter to an SACommand, and optionally, its mapping to a DataSet column.")

