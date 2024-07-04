<!-- loioa57d411084f21015969acd7d63bcc34c -->

# RTRIM Function \[String\] for Data Lake Relational Engine

Returns a string, trimmed of all the trailing characters present in the trim character set.



```
RTRIM ( <string-expression>, [ <trim_character_set> ] );
```



<a name="loioa57d411084f21015969acd7d63bcc34c__RTRIM_parm1"/>

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



<a name="loioa57d411084f21015969acd7d63bcc34c__RTRIM_returns1"/>

## Result Set

Trimmed string.



<a name="loioa57d411084f21015969acd7d63bcc34c__RTRIM_remarks1"/>

## Remarks

If trim character set is not specified, all training spaces in the string expression are trimmed.



<a name="loioa57d411084f21015969acd7d63bcc34c__RTRIM_standards1"/>

## Standards and Compatibility

-   STANDARD function



<a name="loioa57d411084f21015969acd7d63bcc34c__RTRIM_example1"/>

## Examples

The following statement removes all trailing `a` and `b` characters from the given string and returns the value `babababAabend`.

```
SELECT RTRIM ('babababAabendbababab','ab') "rtrim" FROM iq_dummy;
```

**Related Information**  


[LTRIM Function \[String\] for Data Lake Relational Engine](ltrim-function-string-for-data-lake-relational-engine-a561eaf.md "Returns a string, trimmed of all the leading characters present in the trim character set.")

[TRIM Function \[String\] for Data Lake Relational Engine](trim-function-string-for-data-lake-relational-engine-a58b326.md "Returns a string, trimmed of all the leading and trailing characters present in the trim character set.")

[RTRIM Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/3b49f57802c0438a98d16f1b572609ac.html "Returns a string, trimmed of all the trailing characters present in the trim character set.") :arrow_upper_right:

