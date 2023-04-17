<!-- loioa57b364f84f210158a90b2b566be1d36 -->

# RIGHT Function \[String\] for Data Lake Relational Engine

Returns the rightmost characters of a string.



```
RIGHT ( <string-expression>, <numeric-expression> )
```



<a name="loioa57b364f84f210158a90b2b566be1d36__RIGHT_parm1"/>

## Parameters

 *<string-expression\>*
 :   The string to be left-truncated.

  *<numeric-expression\>*
 :   The number of characters at the end of the string to return.

 

<a name="loioa57b364f84f210158a90b2b566be1d36__RIGHT_returns1"/>

## Returns

-   LONG VARCHAR
-   LONG NVARCHAR



<a name="loioa57b364f84f210158a90b2b566be1d36__RIGHT_remarks1"/>

## Remarks

If the string contains multibyte characters, and the proper collation is being used, the number of bytes returned might be greater than the specified number of characters.

> ### Note:  
> The result data type is a `LONG VARCHAR`. If you use `RIGHT` in a `SELECT INTO` statement, you must use `CAST` and set `RIGHT` to the correct data type and size.



<a name="loioa57b364f84f210158a90b2b566be1d36__RIGHT_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – compatible with SAP Adaptive Server Enterprise



<a name="loioa57b364f84f210158a90b2b566be1d36__RIGHT_example1"/>

## Example

The following statement returns the value "olate":

```
SELECT RIGHT( 'chocolate', 5 ) FROM iq_dummy
```

**Related Information**  


[LCASE Function \[String\] for Data Lake Relational Engine](lcase-function-string-for-data-lake-relational-engine-a55c82d.md "Converts all characters in a string to lowercase.")

[LEFT Function \[String\] for Data Lake Relational Engine](left-function-string-for-data-lake-relational-engine-a55d883.md "Returns a specified number of characters from the beginning of a string.")

[LOWER Function \[String\] for Data Lake Relational Engine](lower-function-string-for-data-lake-relational-engine-a561324.md "Converts all characters in a string to lowercase.")

[REPLACE Function \[String\] for Data Lake Relational Engine](replace-function-string-for-data-lake-relational-engine-a579952.md "Replaces all occurrences of a substring with another substring.")

[REVERSE Function \[String\] for Data Lake Relational Engine](reverse-function-string-for-data-lake-relational-engine-a57a972.md "Takes one argument as an input of type BINARY or STRING and returns the specified string with characters listed in reverse order.")

[UCASE Function \[String\] for Data Lake Relational Engine](ucase-function-string-for-data-lake-relational-engine-a58c382.md "Converts all characters in a string to uppercase.")

[UPPER Function \[String\] for Data Lake Relational Engine](upper-function-string-for-data-lake-relational-engine-a58cbc0.md "Converts all characters in a string to uppercase.")

[RIGHT Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/03fba12b431c4d80bcb8933cd7e984ab.html "Returns the rightmost characters of a string.") :arrow_upper_right:

