<!-- loioa537928a84f210158191ea44ca58ee8e -->

# BIT\_LENGTH Function \[String\] for Data Lake Relational Engine

Returns an unsigned 64-bit value containing the bit length of the column parameter.



```
BIT_LENGTH( <column-name> );
```



<a name="loioa537928a84f210158191ea44ca58ee8e__BIT_LENGTH_parm1"/>

## Parameters


<dl>
<dt><b>

*<column-name\>*

</b></dt>
<dd>

The name of a column



</dd>
</dl>



<a name="loioa537928a84f210158191ea44ca58ee8e__BIT_LENGTH_returns1"/>

## Result Set

INT



<a name="loioa537928a84f210158191ea44ca58ee8e__BIT_LENGTH_remarks1"/>

## Remarks

The return value of a NULL argument is NULL.

The `BIT_LENGTH` function supports all data lake Relational Engine data types.



### Unstructured Data Analytics

`BIT_LENGTH` returns an unsigned 64-bit value containing the bit length of the large object column or variable parameter. Use the following syntax, where *<large-object-column\>* is the name of a `LONG VARCHAR` or `LONG BINARY` column or variable:

```
BIT_LENGTH( <large-object-column> );
```

The `BIT_LENGTH` function supports all data lake Relational Engine data types and `LONG BINARY` and `LONG VARCHAR` variables of any size of data, and returns an unsigned 64-bit value containing the bit length of the large object column or variable parameter.



<a name="loioa537928a84f210158191ea44ca58ee8e__BIT_LENGTH_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar

**Related Information**  


[String Functions in Data Lake Relational Engine](string-functions-in-data-lake-relational-engine-a52d1d9.md "String functions perform conversion, extraction, or manipulation operations on strings, or return information about strings.")

[Function Support of Large Object Data](https://help.sap.com/viewer/a8937bea84f21015a80bc776cf758d50/2023_4_QRC/en-US/a60363a384f21015a7f7bc6286516522.html "Learn about the functions that support the LONG BINARY and LONG VARCHAR data types.") :arrow_upper_right:

