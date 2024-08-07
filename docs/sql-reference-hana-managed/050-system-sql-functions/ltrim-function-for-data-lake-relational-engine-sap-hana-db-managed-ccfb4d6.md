<!-- loioccfb4d6a182f4c7badbe8d4f597b316a -->

# LTRIM Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns a string, trimmed of all the leading characters present in the trim character set.



```
LTRIM ( <string-expression>, [ <trim_character_set> ] );
```



<a name="loioccfb4d6a182f4c7badbe8d4f597b316a__section_b2f_x5g_trb"/>

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



<a name="loioccfb4d6a182f4c7badbe8d4f597b316a__section_unc_1vg_trb"/>

## Result Set

Trimmed string.



<a name="loioccfb4d6a182f4c7badbe8d4f597b316a__section_srl_1vg_trb"/>

## Remarks

If trim character set is not specified, all leading spaces in the string expression are trimmed.



<a name="loioccfb4d6a182f4c7badbe8d4f597b316a__section_r3y_5m3_wrb"/>

## Examples

The following statement removes all leading `a` and `b` characters from the given string and returns the value `Aabend`.

```
SELECT LTRIM ('babababAabend','ab') "ltrim" FROM iq_dummy;
```

**Related Information**  


[LTRIM Function \[String\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a561eaf184f2101596bab303110c20fb.html "Returns a string, trimmed of all the leading characters present in the trim character set.") :arrow_upper_right:

