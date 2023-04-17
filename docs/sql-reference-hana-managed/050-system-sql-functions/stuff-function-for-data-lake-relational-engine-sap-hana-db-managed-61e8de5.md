<!-- loio61e8de5f839d426fb531c723d03acddb -->

# STUFF Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Deletes a number of characters from one string and replaces them with another string.



```
STUFF ( <string-expression1>, <start>, <length>, <string-expression2> )
```



<a name="loio61e8de5f839d426fb531c723d03acddb__section_dfk_xr5_vrb"/>

## Parameters

 *<string-expression1\>*
 :   The string to be modified by the `STUFF` function.

  *<start\>*
 :   The character position at which to begin deleting characters. The first character in the string is position 1.

  *<length\>*
 :   The number of characters to delete.

  *<string-expression2\>*
 :   The string to be inserted. To delete a portion of a string using the `STUFF` function, use a replacement string of NULL

 

<a name="loio61e8de5f839d426fb531c723d03acddb__section_uw1_yr5_vrb"/>

## Returns

LONG VARCHAR or LONG BINARY, depending on the data type of the input expressions.



<a name="loio61e8de5f839d426fb531c723d03acddb__section_sgl_yr5_vrb"/>

## Remarks

To delete a portion of a string using `STUFF`, use a replacement string of NULL. To insert a string using `STUFF`, use a length of zero.

The `STUFF` function will return a NULL result in the following situations:

-   Any of the first three parameters is a NULL value.
-   Either the start or length parameter is a negative value.
-   The start parameter is greater than the length of string-expression1.



<a name="loio61e8de5f839d426fb531c723d03acddb__section_lvy_yr5_vrb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – compatible with SAP Adaptive Server Enterprise



<a name="loio61e8de5f839d426fb531c723d03acddb__section_lrn_zr5_vrb"/>

## Example

The following statement returns the value “chocolate pie”:

```
SELECT STUFF( 'chocolate cake', 11, 4, 'pie' )
FROM iq_dummy
```

**Related Information**  


[STUFF Function [String] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a58705b984f21015b314be7887f1392a.html "Deletes a number of characters from one string and replaces them with another string.") :arrow_upper_right:
