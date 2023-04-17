<!-- loioa552c1cc84f21015bfc3d6309d6785d6 -->

# FLOOR Function \[Numeric\] for Data Lake Relational Engine

Returns the floor of \(largest integer not greater than\) a number.



```
FLOOR ( <numeric-expression> )
```



<a name="loioa552c1cc84f21015bfc3d6309d6785d6__FLOOR_parm1"/>

## Parameters

 *<numeric-expression\>*
 :   The number, usually a float.

 

<a name="loioa552c1cc84f21015bfc3d6309d6785d6__FLOOR_returns1"/>

## Returns

DOUBLE



<a name="loioa552c1cc84f21015bfc3d6309d6785d6__FLOOR_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa552c1cc84f21015bfc3d6309d6785d6__FLOOR_examples1"/>

## Examples

-   The following statement returns the value 123.00:

    ```
    SELECT FLOOR ( 123 ) FROM iq_dummy
    ```

-   The following statement returns the value 123:

    ```
    SELECT FLOOR ( 123.45 ) FROM iq_dummy
    ```

-   The following statement returns the value -124.00:

    ```
    SELECT FLOOR ( -123.45 ) FROM iq_dummy
    ```


**Related Information**  


[CEIL Function \[Numeric\] for Data Lake Relational Engine](ceil-function-numeric-for-data-lake-relational-engine-a53a419.md "Returns the smallest integer greater than or equal to the specified expression.")

[CEILING Function \[Numeric\] for Data Lake Relational Engine](ceiling-function-numeric-for-data-lake-relational-engine-a53acd1.md "Returns the ceiling (smallest integer not less than) of a number.")

[FLOOR Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/0beceabbce184f14a1a3fd1482727a2d.html "Returns the floor of (largest integer not greater than) a number.") :arrow_upper_right:

