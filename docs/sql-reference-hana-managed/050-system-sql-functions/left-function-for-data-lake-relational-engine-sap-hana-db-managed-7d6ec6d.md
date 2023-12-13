<!-- loio7d6ec6d7cc0f4bebb844b85a3965a81a -->

# LEFT Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns a specified number of characters from the beginning of a string.



```
LEFT ( <string-expression>, <numeric-expression> );
```



<a name="loio7d6ec6d7cc0f4bebb844b85a3965a81a__section_jhm_1dh_trb"/>

## Parameters


<dl>
<dt><b>

*<string-expression\>*

</b></dt>
<dd>

The string.



</dd><dt><b>

*<numeric-expression\>*

</b></dt>
<dd>

The number of characters to return.



</dd>
</dl>



<a name="loio7d6ec6d7cc0f4bebb844b85a3965a81a__section_cd1_bdh_trb"/>

## Result Set

-   LONG VARCHAR
-   LONG NVARCHAR



<a name="loio7d6ec6d7cc0f4bebb844b85a3965a81a__section_zpn_bdh_trb"/>

## Remarks

The result data type is a LONG VARCHAR. If you use LEFT in a SELECT INTO statement, you must use CAST and set LEFT to the correct data type and size.

If the string contains multibyte characters, and the proper collation is being used, the number of bytes returned may be greater than the specified number of characters.

> ### Note:  
> The result data type of a LEFT function is a LONG VARCHAR. If you use LEFT in a SELECT INTO statement, you need to use CAST and set LEFT to the correct data type and size.



<a name="loio7d6ec6d7cc0f4bebb844b85a3965a81a__section_shk_cdh_trb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loio7d6ec6d7cc0f4bebb844b85a3965a81a__section_dky_cdh_trb"/>

## Example

The following statement returns the value "choco":

```
SELECT LEFT( 'chocolate', 5 ) FROM iq_dummy;
```

**Related Information**  


[LEFT Function \[String\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/a55d883284f210158c5ec15e3e69239f.html "Returns a specified number of characters from the beginning of a string.") :arrow_upper_right:

