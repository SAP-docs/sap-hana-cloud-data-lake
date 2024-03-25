<!-- loioa53acd1c84f21015822dd5e02d6dc9cc -->

# CEILING Function \[Numeric\] for Data Lake Relational Engine

Returns the ceiling \(smallest integer not less than\) of a number.



```
CEILING ( <numeric-expression> );
```



<a name="loioa53acd1c84f21015822dd5e02d6dc9cc__CEILING_parm1"/>

## Parameters


<dl>
<dt><b>

*<numeric-expression\>*

</b></dt>
<dd>

The number that has the ceiling to be calculated.



</dd>
</dl>



<a name="loioa53acd1c84f21015822dd5e02d6dc9cc__CEILING_returns1"/>

## Result Set

DOUBLE



<a name="loioa53acd1c84f21015822dd5e02d6dc9cc__CEILING_remarks1"/>

## Remarks

`CEIL` is a synonym for `CEILING`.



<a name="loioa53acd1c84f21015822dd5e02d6dc9cc__CEILING_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa53acd1c84f21015822dd5e02d6dc9cc__CEILING_examples1"/>

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


[FLOOR Function \[Numeric\] for Data Lake Relational Engine](floor-function-numeric-for-data-lake-relational-engine-a552c1c.md "Returns the floor of (largest integer not greater than) a number.")

[CEIL Function \[Numeric\] for Data Lake Relational Engine](ceil-function-numeric-for-data-lake-relational-engine-a53a419.md "Returns the smallest integer greater than or equal to the specified expression.")

[CEILING Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/2201fadee98e4d80a4952cdf3e105c65.html "Returns the ceiling (smallest integer not less than) of a number.") :arrow_upper_right:

