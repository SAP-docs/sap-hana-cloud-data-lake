<!-- loioa58787e784f21015acc5ecadf5b1a9a0 -->

# SUBSTRING Function \[String\] for Data Lake Relational Engine

Returns a substring of a string.



```
{ SUBSTRING | SUBSTR } ( <string-expression>, <start> [ , <length> ] )
```



<a name="loioa58787e784f21015acc5ecadf5b1a9a0__SUBSTRING_parm1"/>

## Parameters


<dl>
<dt><b>

*<string-expression\>*

</b></dt>
<dd>

The string from which a substring is to be returned.



</dd><dt><b>

*<start\>*

</b></dt>
<dd>

The start position of the substring to return, in characters. A negative starting position specifies a number of characters from the end of the string instead of the beginning. The first character in the string is at position 1.



</dd><dt><b>

*<length\>*

</b></dt>
<dd>

The length of the substring to return, in characters:

-   A positive *<length\>* specifies that the substring ends *<length\>* characters to the right of the starting position.
-   A negative *<length\>* specifies that the substring ends *<length\>* characters to the left of the starting position.



</dd>
</dl>



<a name="loioa58787e784f21015acc5ecadf5b1a9a0__SUBSTRING_returns1"/>

## Returns

-   LONG BINARY
-   LONG NVARCHAR
-   LONG VARCHAR

> ### Note:  
> The result data type is a `LONG VARCHAR`. If you use `STRING` in a `SELECT INTO` statement, you must use `CAST` and set `STRING` to the correct data type and size.



<a name="loioa58787e784f21015acc5ecadf5b1a9a0__SUBSTRING_remarks1"/>

## Remarks

If *<length\>* is specified, the substring is restricted to that length. If no length is specified, the remainder of the string is returned, starting at the *<start\>* position.

Both *<start\>* and *<length\>* can be negative. Using appropriate combinations of negative and positive numbers, you can get a substring from either the beginning or end of the string.

When the `ansi_substring` database option is set to ON \(default\), negative values are invalid.



<a name="loioa58787e784f21015acc5ecadf5b1a9a0__SUBSTRING_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar.
-   SAP database products – SAP Adaptive Server Enterprise does not support `SUBSTR`; use `SUBSTRING` instead.



<a name="loioa58787e784f21015acc5ecadf5b1a9a0__SUBSTRING_examples1"/>

## Example

-   The following statement returns ***back***:

    ```
    SELECT SUBSTRING ( 'back yard', 1 , 4 )
      FROM iq_dummy
    ```

-   The following statement returns ***yard***:

    ```
    SELECT SUBSTR ( 'back yard', -1 , -4 )
      FROM iq_dummy
    ```

-   The following statement returns ***0x2233***:

    ```
    SELECT SUBSTR ( 0x112233445566, 2, 2 )
      FROM iq_dummy
    ```


**Related Information**  


[ANSI\_SUBSTRING Option \[TSQL\] for Data Lake Relational Engine](../090-database-options/ansi-substring-option-tsql-for-data-lake-relational-engine-a62ceea.md "Controls the behavior of the SUBSTRING (SUBSTR) function when negative values are provided for the start or length parameters.")

[CHARINDEX Function \[String\] for Data Lake Relational Engine](charindex-function-string-for-data-lake-relational-engine-a53cde2.md "Returns the position of the first occurrence of a specified string in another string.")

[SUBSTRING Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/f114d3543b9c48f69b269b951d549034.html "Returns a substring of a string.") :arrow_upper_right:

