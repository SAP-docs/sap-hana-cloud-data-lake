<!-- loio03fba12b431c4d80bcb8933cd7e984ab -->

# RIGHT Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the rightmost characters of a string.



```
RIGHT ( <string-expression>, <numeric-expression> );
```



<a name="loio03fba12b431c4d80bcb8933cd7e984ab__section_kgp_gtt_vrb"/>

## Parameters


<dl>
<dt><b>

*<string-expression\>*

</b></dt>
<dd>

The string to be left-truncated.



</dd><dt><b>

*<numeric-expression\>*

</b></dt>
<dd>

The number of characters at the end of the string to return.



</dd>
</dl>



<a name="loio03fba12b431c4d80bcb8933cd7e984ab__section_yk1_htt_vrb"/>

## Result Set

-   LONG VARCHAR
-   LONG NVARCHAR



<a name="loio03fba12b431c4d80bcb8933cd7e984ab__section_isl_c43_wrb"/>

## Remarks

If the string contains multibyte characters, and the proper collation is being used, the number of bytes returned might be greater than the specified number of characters.

> ### Note:  
> The result data type is a `LONG VARCHAR`. If you use `RIGHT` in a `SELECT INTO` statement, you must use `CAST` and set `RIGHT` to the correct data type and size.



<a name="loio03fba12b431c4d80bcb8933cd7e984ab__section_qz1_d43_wrb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – compatible with SAP Adaptive Server Enterprise



<a name="loio03fba12b431c4d80bcb8933cd7e984ab__section_cb3_3tt_vrb"/>

## Example

The following statement returns the value "olate":

```
SELECT RIGHT( 'chocolate', 5 ) FROM iq_dummy;
```

**Related Information**  


[RIGHT Function \[String\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/a57b364f84f210158a90b2b566be1d36.html "Returns the rightmost characters of a string.") :arrow_upper_right:

