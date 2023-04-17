<!-- loioa58b326684f210158b01c6a84254a2f2 -->

# TRIM Function \[String\] for Data Lake Relational Engine

Returns a string, trimmed of all the leading and trailing characters present in the trim character set.



```
TRIM ( <string-expression>, [ <trim_character_set> ] )
```



<a name="loioa58b326684f210158b01c6a84254a2f2__TRIM_parm1"/>

## Parameters

 *<string-expression\>*
 :   The string to be trimmed.

  *<trim\_character\_set\>*
 :   The set of characters to use for trim.

 

<a name="loioa58b326684f210158b01c6a84254a2f2__TRIM_returns1"/>

## Returns

Trimmed string.



<a name="loioa58b326684f210158b01c6a84254a2f2__TRIM_standards1"/>

## Standards and Compatibility

-   STANDARD function.



<a name="loioa58b326684f210158b01c6a84254a2f2__TRIM_examples1"/>

## Example

The following statement removes all leading and trailing `a` and `b` characters from the given string and returns the value `Aabend`.

```
SELECT TRIM ('babababENDbababa','ab') "trim" FROM iq_dummy
```

**Related Information**  


[LTRIM Function \[String\] for Data Lake Relational Engine](ltrim-function-string-for-data-lake-relational-engine-a561eaf.md "Returns a string, trimmed of all the leading characters present in the trim character set.")

[RTRIM Function \[String\] for Data Lake Relational Engine](rtrim-function-string-for-data-lake-relational-engine-a57d411.md "Returns a string, trimmed of all the trailing characters present in the trim character set.")

[TRIM Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/d07890fd143c474c99313bda01aae897.html "Returns a string, trimmed of all the leading and trailing characters present in the trim character set.") :arrow_upper_right:

