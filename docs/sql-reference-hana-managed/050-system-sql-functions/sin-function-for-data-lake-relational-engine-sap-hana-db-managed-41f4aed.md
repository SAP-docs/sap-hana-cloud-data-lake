<!-- loio41f4aed677bc4981bfab2a667390fe1a -->

# SIN Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the sine of a number, expressed in radians.



```
SIN ( <numeric-expression> );
```



<a name="loio41f4aed677bc4981bfab2a667390fe1a__section_gkb_my5_vrb"/>

## Parameters


<dl>
<dt><b>

*<numeric-expression\>*

</b></dt>
<dd>

The angle, in radians.



</dd>
</dl>



<a name="loio41f4aed677bc4981bfab2a667390fe1a__section_nt4_my5_vrb"/>

## Result Set

DOUBLE



<a name="loio41f4aed677bc4981bfab2a667390fe1a__section_d4x_my5_vrb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loio41f4aed677bc4981bfab2a667390fe1a__section_sfl_ny5_vrb"/>

## Example

The following statement returns the value 0.496880:

```
SELECT SIN( 0.52 ) FROM iq_dummy;
```

**Related Information**  


[SIN Function \[Numeric\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/a57fd70a84f21015a70cd54791443340.html "Returns the sine of a number, expressed in radians.") :arrow_upper_right:

