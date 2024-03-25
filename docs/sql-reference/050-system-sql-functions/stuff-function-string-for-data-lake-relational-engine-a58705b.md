<!-- loioa58705b984f21015b314be7887f1392a -->

# STUFF Function \[String\] for Data Lake Relational Engine

Deletes a number of characters from one string and replaces them with another string.



```
STUFF ( <string-expression1>, <start>, <length>, <string-expression2> );
```



<a name="loioa58705b984f21015b314be7887f1392a__STUFF_parm1"/>

## Parameters


<dl>
<dt><b>

*<string-expression1\>*

</b></dt>
<dd>

The string to be modified by the `STUFF` function.



</dd><dt><b>

*<start\>*

</b></dt>
<dd>

The character position at which to begin deleting characters. The first character in the string is position 1.



</dd><dt><b>

*<length\>*

</b></dt>
<dd>

The number of characters to delete.



</dd><dt><b>

*<string-expression2\>*

</b></dt>
<dd>

The string to be inserted. To delete a portion of a string using the `STUFF` function, use a replacement string of NULL



</dd>
</dl>



<a name="loioa58705b984f21015b314be7887f1392a__STUFF_returns1"/>

## Result Set

LONG VARCHAR or LONG BINARY, depending on the data type of the input expressions.



<a name="loioa58705b984f21015b314be7887f1392a__STUFF_remarks1"/>

## Remarks

To delete a portion of a string using `STUFF`, use a replacement string of NULL. To insert a string using `STUFF`, use a length of zero.

The `STUFF` function will return a NULL result in the following situations:

-   Any of the first three parameters is a NULL value.
-   Either the start or length parameter is a negative value.
-   The start parameter is greater than the length of string-expression1.



<a name="loioa58705b984f21015b314be7887f1392a__STUFF_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – compatible with SAP Adaptive Server Enterprise



<a name="loioa58705b984f21015b314be7887f1392a__STUFF_example1"/>

## Example

The following statement returns the value “chocolate pie”:

```
SELECT STUFF( 'chocolate cake', 11, 4, 'pie' )
FROM iq_dummy;
```

**Related Information**  


[INSERTSTR Function \[String\] for Data Lake Relational Engine](insertstr-function-string-for-data-lake-relational-engine-a558eff.md "Inserts a string into another string at a specified position.")

[REPLACE Function \[String\] for Data Lake Relational Engine](replace-function-string-for-data-lake-relational-engine-a579952.md "Replaces all occurrences of a substring with another substring.")

[STUFF Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/61e8de5f839d426fb531c723d03acddb.html "Deletes a number of characters from one string and replaces them with another string.") :arrow_upper_right:

