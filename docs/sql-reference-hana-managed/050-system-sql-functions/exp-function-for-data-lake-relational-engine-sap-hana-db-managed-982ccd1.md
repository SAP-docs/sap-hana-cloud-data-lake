<!-- loio982ccd1f2f84468d9753761e3be45fca -->

# EXP Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the exponential function, e, to the power of a number.



```
EXP ( <numeric-expression> );
```



<a name="loio982ccd1f2f84468d9753761e3be45fca__section_exk_2sg_trb"/>

## Parameters


<dl>
<dt><b>

*<numeric-expression\>*

</b></dt>
<dd>

The exponent.



</dd>
</dl>



<a name="loio982ccd1f2f84468d9753761e3be45fca__section_msw_2sg_trb"/>

## Result Set

DOUBLE



<a name="loio982ccd1f2f84468d9753761e3be45fca__section_wcj_fsg_trb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loio982ccd1f2f84468d9753761e3be45fca__section_qjv_fsg_trb"/>

## Example

The following statement returns the value 3269017.3724721107:

```
SELECT EXP( 15 ) FROM iq_dummy;
```

**Related Information**  


[EXP Function \[Numeric\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/a55131d984f21015966fac9e1cb19b02.html "Returns the exponential function, e, to the power of a number.") :arrow_upper_right:

