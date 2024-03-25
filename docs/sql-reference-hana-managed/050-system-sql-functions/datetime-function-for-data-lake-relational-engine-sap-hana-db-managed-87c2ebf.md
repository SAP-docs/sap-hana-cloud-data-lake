<!-- loio87c2ebfc15364ff0b9b4e7dc0fa66207 -->

# DATETIME Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Converts an expression into a timestamp.



```
DATETIME ( <expression> );
```



<a name="loio87c2ebfc15364ff0b9b4e7dc0fa66207__section_ujh_3cm_srb"/>

## Parameters


<dl>
<dt><b>

*<expression\>*

</b></dt>
<dd>

The expression to be converted. The expression is usually a string. Conversion errors may be reported.



</dd>
</dl>



<a name="loio87c2ebfc15364ff0b9b4e7dc0fa66207__section_hp5_3cm_srb"/>

## Result Set

TIMESTAMP



<a name="loio87c2ebfc15364ff0b9b4e7dc0fa66207__section_k3k_jcm_srb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loio87c2ebfc15364ff0b9b4e7dc0fa66207__section_esw_jcm_srb"/>

## Example

The following statement returns a timestamp with value 1998-09-09 12:12:12.000:

```
SELECT DATETIME( '1998-09-09 12:12:12.000' ) FROM iq_dummy;
```

**Related Information**  


[DATETIME Function \[Date and Time\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/a548c21f84f210158350cf2fab822610.html "Converts an expression into a timestamp.") :arrow_upper_right:

