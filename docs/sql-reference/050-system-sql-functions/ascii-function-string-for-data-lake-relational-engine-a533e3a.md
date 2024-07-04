<!-- loioa533e3a684f21015a2a0af73e4a9ad1c -->

# ASCII Function \[String\] for Data Lake Relational Engine

Returns the integer ASCII value of the first byte in a *<string-expression\>*.



```
ASCII ( <string-expression> );
```



<a name="loioa533e3a684f21015a2a0af73e4a9ad1c__ASCII_parm1"/>

## Parameters


<dl>
<dt><b>

*<string-expression\>*

</b></dt>
<dd>

The string.



</dd>
</dl>



<a name="loioa533e3a684f21015a2a0af73e4a9ad1c__ASCII_returns1"/>

## Result Set

SMALLINT



<a name="loioa533e3a684f21015a2a0af73e4a9ad1c__ASCII_remarks1"/>

## Remarks

If the string is empty, `ASCII` returns zero. Literal strings must be enclosed in quotes.



<a name="loioa533e3a684f21015a2a0af73e4a9ad1c__ASCII_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa533e3a684f21015a2a0af73e4a9ad1c__ASCII_examples1"/>

## Examples

The following statement returns the value 90, when the collation sequence is set to the default ISO\_BINENG:

```
SELECT ASCII( 'Z' ) FROM iq_dummy;
```

**Related Information**  


[ASCII Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/554cede3499a4ef98a05be128493031f.html "Returns the integer ASCII value of the first byte in a string-expression.") :arrow_upper_right:

