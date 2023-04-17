<!-- loio3c1b3e0c6c5f101485f4e46df98bfd6a -->

# Precision Property

Gets and sets the maximum number of digits used to represent the Value property.



Visual Basic
:   ```
Public Property Precision As Byte
```

C\#
:   ```
public byte Precision {get;set;}
```



## Remarks

The value of this property is the maximum number of digits used to represent the Value property. The default value is 0, which indicates that the data provider sets the precision for the Value property.

The Precision property is only used for decimal and numeric input parameters.

