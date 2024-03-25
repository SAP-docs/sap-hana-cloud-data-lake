<!-- loio2201fadee98e4d80a4952cdf3e105c65 -->

# CEILING Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the ceiling \(smallest integer not less than\) of a number.



```
CEILING ( <numeric-expression> );
```



<a name="loio2201fadee98e4d80a4952cdf3e105c65__section_bm4_wtl_srb"/>

## Parameters


<dl>
<dt><b>

*<numeric-expression\>*

</b></dt>
<dd>

The number that has the ceiling to be calculated.



</dd>
</dl>



<a name="loio2201fadee98e4d80a4952cdf3e105c65__section_krc_xtl_srb"/>

## Result Set

DOUBLE



<a name="loio2201fadee98e4d80a4952cdf3e105c65__section_e3t_xtl_srb"/>

## Remarks

`CEIL` is a synonym for `CEILING`.



<a name="loio2201fadee98e4d80a4952cdf3e105c65__section_n4d_ytl_srb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loio2201fadee98e4d80a4952cdf3e105c65__section_hvq_ytl_srb"/>

## Examples

-   The following statement returns the value 60.00000:

    ```
    SELECT CEILING( 59.84567 ) FROM iq_dummy;
    ```

-   The following statement returns the value 123:

    ```
    SELECT CEILING( 123 ) FROM iq_dummy;
    ```

-   The following statement returns the value 124.00:

    ```
    SELECT CEILING( 123.45 ) FROM iq_dummy;
    ```

-   The following statement returns the value -123.00:

    ```
    SELECT CEILING( -123.45 ) FROM iq_dummy;
    ```


**Related Information**  


[CEIL Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](ceil-function-for-data-lake-relational-engine-sap-hana-db-managed-cf884ae.md "Returns the smallest integer greater than or equal to the specified expression.")

[CEILING Function \[Numeric\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/a53acd1c84f21015822dd5e02d6dc9cc.html "Returns the ceiling (smallest integer not less than) of a number.") :arrow_upper_right:

