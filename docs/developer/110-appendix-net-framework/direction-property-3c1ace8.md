<!-- loio3c1ace896c5f10149eaa9b96ef5e6ef2 -->

# Direction Property

Gets and sets a value indicating whether the parameter is input-only, output-only, bidirectional, or a stored procedure return value parameter.



Visual Basic
:   ```
Public Overrides Property Direction As ParameterDirection
```

C\#
:   ```
public override ParameterDirection Direction {get;set;}
```



## Remarks

One of the ParameterDirection values.

If the ParameterDirection is output, and execution of the associated SACommand does not return a value, then the SAParameter contains a null value. After the last row from the last result set is read, the Output, InputOut, and ReturnValue parameters are updated.

