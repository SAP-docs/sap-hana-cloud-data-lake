<!-- loioa55d883284f210158c5ec15e3e69239f -->

# LEFT Function \[String\] for Data Lake Relational Engine

Returns a specified number of characters from the beginning of a string.



```
LEFT ( <string-expression>, <numeric-expression> )
```



<a name="loioa55d883284f210158c5ec15e3e69239f__LEFT_parm1"/>

## Parameters


<dl>
<dt><b>

*<string-expression\>*

</b></dt>
<dd>

The string.



</dd><dt><b>

*<numeric-expression\>*

</b></dt>
<dd>

The number of characters to return.



</dd>
</dl>



<a name="loioa55d883284f210158c5ec15e3e69239f__LEFT_returns1"/>

## Returns

-   LONG VARCHAR
-   LONG NVARCHAR



<a name="loioa55d883284f210158c5ec15e3e69239f__LEFT_remarks1"/>

## Remarks

The result data type is a LONG VARCHAR. If you use LEFT in a SELECT INTO statement, you must use CAST and set LEFT to the correct data type and size.

If the string contains multibyte characters, and the proper collation is being used, the number of bytes returned may be greater than the specified number of characters.

> ### Note:  
> The result data type of a LEFT function is a LONG VARCHAR. If you use LEFT in a SELECT INTO statement, you need to use CAST and set LEFT to the correct data type and size.



<a name="loioa55d883284f210158c5ec15e3e69239f__LEFT_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa55d883284f210158c5ec15e3e69239f__LEFT_example1"/>

## Example

The following statement returns the value "choco":

```
SELECT LEFT( 'chocolate', 5 ) FROM iq_dummy
```

**Related Information**  


[LCASE Function \[String\] for Data Lake Relational Engine](lcase-function-string-for-data-lake-relational-engine-a55c82d.md "Converts all characters in a string to lowercase.")

[LOWER Function \[String\] for Data Lake Relational Engine](lower-function-string-for-data-lake-relational-engine-a561324.md "Converts all characters in a string to lowercase.")

[REPLACE Function \[String\] for Data Lake Relational Engine](replace-function-string-for-data-lake-relational-engine-a579952.md "Replaces all occurrences of a substring with another substring.")

[REVERSE Function \[String\] for Data Lake Relational Engine](reverse-function-string-for-data-lake-relational-engine-a57a972.md "Takes one argument as an input of type BINARY or STRING and returns the specified string with characters listed in reverse order.")

[RIGHT Function \[String\] for Data Lake Relational Engine](right-function-string-for-data-lake-relational-engine-a57b364.md "Returns the rightmost characters of a string.")

[UCASE Function \[String\] for Data Lake Relational Engine](ucase-function-string-for-data-lake-relational-engine-a58c382.md "Converts all characters in a string to uppercase.")

[UPPER Function \[String\] for Data Lake Relational Engine](upper-function-string-for-data-lake-relational-engine-a58cbc0.md "Converts all characters in a string to uppercase.")

[LEFT Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/7d6ec6d7cc0f4bebb844b85a3965a81a.html "Returns a specified number of characters from the beginning of a string.") :arrow_upper_right:

