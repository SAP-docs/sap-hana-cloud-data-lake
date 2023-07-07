<!-- loiod07890fd143c474c99313bda01aae897 -->

# TRIM Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns a string, trimmed of all the leading and trailing characters present in the trim character set.



```
TRIM ( <string-expression>, [ <trim_character_set> ] )
```



<a name="loiod07890fd143c474c99313bda01aae897__section_ihc_v3v_vrb"/>

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



<a name="loiod07890fd143c474c99313bda01aae897__section_t4q_v3v_vrb"/>

## Returns

Trimmed string.



<a name="loiod07890fd143c474c99313bda01aae897__section_wnc_w3v_vrb"/>

## Standards and Compatibility

-   STANDARD function.



<a name="loiod07890fd143c474c99313bda01aae897__section_ehm_w3v_vrb"/>

## Example

The following statement removes all leading and trailing `a` and `b` characters from the given string and returns the value `END`.

```
SELECT TRIM ('babababENDbababa','ab') "trim" FROM iq_dummy
```

**Related Information**  


[TRIM Function [String] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a58b326684f210158b01c6a84254a2f2.html "Returns a string, trimmed of all the leading and trailing characters present in the trim character set.") :arrow_upper_right:

