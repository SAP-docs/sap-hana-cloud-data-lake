<!-- loioc440e3a7627544838259dcfab11a5bd1 -->

# CHAR\_LENGTH Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the number of characters in a string.



```
CHAR_LENGTH ( <string-expression> );
```



<a name="loioc440e3a7627544838259dcfab11a5bd1__section_ngt_zsl_srb"/>

## Parameters


<dl>
<dt><b>

*<string-expression\>*

</b></dt>
<dd>

The string that has the length to be calculated.



</dd>
</dl>



<a name="loioc440e3a7627544838259dcfab11a5bd1__section_e1f_1tl_srb"/>

## Result Set

INT



<a name="loioc440e3a7627544838259dcfab11a5bd1__section_nbr_1tl_srb"/>

## Remarks

Trailing white space characters are included in the length returned.

The return value of a NULL string is NULL.

If the string is in a multibyte character set, the CHAR\_LENGTH value may be less than the BYTE\_LENGTH value.

CHAR\_LENGTH64 also supports LONG VARCHAR variables of any data size.

The CHAR\_LENGTH function supports LONG VARCHAR columns and LONG VARCHAR variables of any size of data. If the character length exceeds 2GB - 1 \(2147483647\), an error is returned.



<a name="loioc440e3a7627544838259dcfab11a5bd1__section_lf3_btl_srb"/>

## Standards and Compatibility

-   SQL – ISO/ANSI SQL compliant



<a name="loioc440e3a7627544838259dcfab11a5bd1__section_ilx_btl_srb"/>

## Example

The following statement returns the value 8:

```
SELECT CHAR_LENGTH( 'Chemical' ) FROM iq_dummy;
```

**Related Information**  


[CHAR_LENGTH Function \[String\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/a53bd3d384f21015bcf88da636a1a768.html "Returns the number of characters in a string.") :arrow_upper_right:

