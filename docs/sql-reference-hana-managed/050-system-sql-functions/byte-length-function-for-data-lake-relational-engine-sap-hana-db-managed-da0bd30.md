<!-- loioda0bd303497b4828b0c89f22e692a6c5 -->

# BYTE\_LENGTH Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the number of bytes in a string.



```
BYTE_LENGTH ( <string-expression> );
```



<a name="loioda0bd303497b4828b0c89f22e692a6c5__section_wfh_tfl_srb"/>

## Parameters


<dl>
<dt><b>

*<string-expression\>*

</b></dt>
<dd>

The string that has the length to be calculated.



</dd>
</dl>



<a name="loioda0bd303497b4828b0c89f22e692a6c5__section_k3t_tfl_srb"/>

## Result Set

INT



<a name="loioda0bd303497b4828b0c89f22e692a6c5__section_hvf_5fl_srb"/>

## Remarks

Trailing white space characters are included in the length returned.

The return value of a NULL string is NULL.

If the string is in a multibyte character set, the `BYTE_LENGTH` value differs from the number of characters returned by `CHAR_LENGTH`.

The `BYTE_LENGTH` function supports both `LONG BINARY` columns and variables and `LONG VARCHAR` columns and variables, only if the query returns less than 2 GB. If the byte length of the returned `LONG BINARY` or `LONG VARCHAR` data is greater than or equal to 2 GB, `BYTE_LENGTH` returns an error that says you must use the `BYTE_LENGTH64` function.



<a name="loioda0bd303497b4828b0c89f22e692a6c5__section_drt_5fl_srb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioda0bd303497b4828b0c89f22e692a6c5__section_hsg_vfl_srb"/>

## Examples

Returns the value 12:

```
SELECT BYTE_LENGTH( 'Test Message' ) FROM iq_dummy;
```

**Related Information**  


[BYTE_LENGTH Function \[String\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a53816b784f210159b849878d71ab1a8.html "Returns the number of bytes in a string.") :arrow_upper_right:

