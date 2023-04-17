<!-- loioa560b1f984f210158a13cb8a24202e26 -->

# LOG10 Function \[Numeric\] for Data Lake Relational Engine

Returns the base 10 logarithm of a number.



```
LOG10 ( <numeric-expression> )
```



<a name="loioa560b1f984f210158a13cb8a24202e26__LOG10_parm1"/>

## Parameters

 *<numeric-expression\>*
 :   The number.

 

<a name="loioa560b1f984f210158a13cb8a24202e26__LOG10_returns1"/>

## Returns

This function converts its argument to DOUBLE, and performs the computation in double-precision floating point. If the parameter is NULL, the result is NULL.



<a name="loioa560b1f984f210158a13cb8a24202e26__LOG10_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa560b1f984f210158a13cb8a24202e26__LOG10_example1"/>

## Example

The following statement returns the value 1.698970:

```
SELECT LOG10( 50 ) FROM iq_dummy
```

**Related Information**  


[LN Function \[Numeric\] for Data Lake Relational Engine](ln-function-numeric-for-data-lake-relational-engine-a55f245.md "Returns the natural logarithm of the specified expression.")

[LOG Function \[Numeric\] for Data Lake Relational Engine](log-function-numeric-for-data-lake-relational-engine-a560332.md "Returns the natural logarithm of a number.")

[LOG10 Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/56b6d539c61b44a3a392d9b8f5ba937c.html "Returns the base 10 logarithm of a number.") :arrow_upper_right:

