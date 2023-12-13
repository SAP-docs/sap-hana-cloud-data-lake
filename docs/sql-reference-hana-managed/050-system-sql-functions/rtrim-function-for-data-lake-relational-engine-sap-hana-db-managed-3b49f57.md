<!-- loio3b49f57802c0438a98d16f1b572609ac -->

# RTRIM Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns a string, trimmed of all the trailing characters present in the trim character set.



```
RTRIM ( <string-expression>, [ <trim_character_set> ] );
```



<a name="loio3b49f57802c0438a98d16f1b572609ac__section_ucs_4qt_vrb"/>

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



<a name="loio3b49f57802c0438a98d16f1b572609ac__section_fyd_pqt_vrb"/>

## Result Set

Trimmed string.



<a name="loio3b49f57802c0438a98d16f1b572609ac__section_ufq_pqt_vrb"/>

## Remarks

If trim character set is not specified, all training spaces in the string expression are trimmed.



<a name="loio3b49f57802c0438a98d16f1b572609ac__section_lx5_343_wrb"/>

## Standards and Compatibility

-   STANDARD function



<a name="loio3b49f57802c0438a98d16f1b572609ac__section_f3b_rqt_vrb"/>

## Example

The following statement removes all trailing `a` and `b` characters from the given string and returns the value `babababAabend`.

```
SELECT RTRIM ('babababAabendbababab','ab') "rtrim" FROM iq_dummy;
```

**Related Information**  


[RTRIM Function \[String\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/a57d411084f21015969acd7d63bcc34c.html "Returns a string, trimmed of all the trailing characters present in the trim character set.") :arrow_upper_right:

