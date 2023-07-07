<!-- loioa55e08c884f210159d0cec6bce940d82 -->

# LEN Function \[String\] for Data Lake Relational Engine

Takes one argument as an input of type BINARY or STRING and returns the number of characters, as defined by the database's collation sequence, of a specified string expression, excluding trailing blanks.



```
LEN ( <string_expr> )
```



<a name="loioa55e08c884f210159d0cec6bce940d82__LEN_parm1"/>

## Parameters


<dl>
<dt><b>

*<string\_expr\>*

</b></dt>
<dd>

The string expression to be evaluated.



</dd>
</dl>



<a name="loioa55e08c884f210159d0cec6bce940d82__LEN_remarks1"/>

## Remarks

The result may differ from the string’s byte length for multi-byte character sets.

BINARY and VARBINARY are also allowed, in which case LEN\(\) returns the number of bytes of the input.

LEN is an alias of LENGTH function

This function is the equivalent of CHAR\_LENGTH \(*<string\_expression \>*\).



<a name="loioa55e08c884f210159d0cec6bce940d82__LEN_standards1"/>

## Standards and Compatibility

SQL – Transact-SQL extension to ISO/ANSI SQL grammar



<a name="loioa55e08c884f210159d0cec6bce940d82__LEN_example1"/>

## Example

The following example returns the value 3152:

```
SELECT LEN(Photo) FROM Products WHERE ID = 500;
```

**Related Information**  


[String Functions in Data Lake Relational Engine](string-functions-in-data-lake-relational-engine-a52d1d9.md "String functions perform conversion, extraction, or manipulation operations on strings, or return information about strings.")

[LEN Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/a895aabb25c84638b38c77cd78d7ad00.html "Takes one argument as an input of type BINARY or STRING and returns the number of characters, as defined by the database&apos;s collation sequence, of a specified string expression, excluding trailing blanks.") :arrow_upper_right:

