<!-- loioa561eaf184f2101596bab303110c20fb -->

# LTRIM Function \[String\] for Data Lake Relational Engine

Returns a string, trimmed of all the leading characters present in the trim character set.



```
LTRIM ( <string-expression>, [ <trim_character_set> ] );
```



<a name="loioa561eaf184f2101596bab303110c20fb__LTRIM_parm1"/>

## Parameters


<dl>
<dt><b>

*<string-expression\>*

</b></dt>
<dd>

The string to be trimmed.



</dd><dt><b>

*<trim\_character\_set\>*

</b></dt>
<dd>

The set of characters to use for trim.



</dd>
</dl>



<a name="loioa561eaf184f2101596bab303110c20fb__LTRIM_returns1"/>

## Result Set

Trimmed string.



<a name="loioa561eaf184f2101596bab303110c20fb__LTRIM_remarks1"/>

## Remarks

If trim character set is not specified, all leading spaces in the string expression are trimmed.



<a name="loioa561eaf184f2101596bab303110c20fb__LTRIM_standards1"/>

## Standards and Compatibility

-   STANDARD function



<a name="loioa561eaf184f2101596bab303110c20fb__LTRIM_examples1"/>

## Examples

The following statement removes all leading `a` and `b` characters from the given string and returns the value `Aabend`.

```
SELECT LTRIM ('babababAabend','ab') "ltrim" FROM iq_dummy;
```

**Related Information**  


[RTRIM Function \[String\] for Data Lake Relational Engine](rtrim-function-string-for-data-lake-relational-engine-a57d411.md "Returns a string, trimmed of all the trailing characters present in the trim character set.")

[TRIM Function \[String\] for Data Lake Relational Engine](trim-function-string-for-data-lake-relational-engine-a58b326.md "Returns a string, trimmed of all the leading and trailing characters present in the trim character set.")

[LTRIM Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/ccfb4d6a182f4c7badbe8d4f597b316a.html "Returns a string, trimmed of all the leading characters present in the trim character set.") :arrow_upper_right:

