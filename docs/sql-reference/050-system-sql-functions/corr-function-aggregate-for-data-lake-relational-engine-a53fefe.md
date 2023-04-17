<!-- loioa53fefea84f21015a7ac9e118cc9795c -->

# CORR Function \[Aggregate\] for Data Lake Relational Engine

Returns the correlation coefficient of a set of number pairs.



 Syntax 1
 :   ```
CORR ( <dependent-expression>, <independent-expression> )
```

  Syntax 2
 :   ```
CORR ( <dependent-expression>, <independent-expression> )
OVER ( <window-spec> )
```

 

<a name="loioa53fefea84f21015a7ac9e118cc9795c__CORR_parm1"/>

## Parameters

 *<dependent-expression\>*
 :   The variable that is affected by the *<independent-expression\>*.

  *<independent-expression\>*
 :   The variable that influences the outcome.

  *<window-spec\>*
 :   Specified when using this function as a window function.

 

<a name="loioa53fefea84f21015a7ac9e118cc9795c__CORR_retunrs1"/>

## Returns

DOUBLE



<a name="loioa53fefea84f21015a7ac9e118cc9795c__CORR_remarks1"/>

## Remarks

The `CORR` function converts its arguments to DOUBLE, performs the computation in double-precision floating-point, and returns a DOUBLE as the result. If applied to an empty set, then CORR returns NULL.

Both *<dependent-expression\>* and *<independent-expression\>* are numeric. The function is applied to the set of \(*<dependent-expression\>*, *<independent-expression\>*\) after eliminating the pairs for which either *<dependent-expression\>* or *<independent-expression\>* is NULL. The following computation is made, where *<x\>* represents the *<dependent-expression\>* and *<y\>* represents the *<independent-expression\>*:

```
COVAR_POP (y, x) / (STDDEV_POP (x) * STDDEV_POP (y))
```

> ### Note:  
> ROLLUP and CUBE are not supported in the GROUP BY clause with Syntax 1.

Syntax 2 – The *<window-spec\>* parameter represents usage as a window function in a `SELECT` statement. As such, you can specify elements of *<window-spec\>* either in the function syntax \(inline\), or with a `WINDOW` clause in the `SELECT` statement.



<a name="loioa53fefea84f21015a7ac9e118cc9795c__CORR_standards1"/>

## Standards and Compatibility

-   SQL – ISO/ANSI SQL compliant. SQL foundation feature outside of core SQL.



<a name="loioa53fefea84f21015a7ac9e118cc9795c__CORR_examples1"/>

## Example

The following example performs a correlation to discover whether age is associated with income level. This function returns the value 0.440227:

```
SELECT CORR( Salary, ( YEAR( NOW( ) ) - YEAR( BirthDate ) ) ) FROM Employees;
```

**Related Information**  


[Windowing Aggregate Function Usage in Data Lake Relational Engine](windowing-aggregate-function-usage-in-data-lake-relational-engine-a527f35.md "A major feature of the ISO/ANSI SQL extensions for OLAP is a construct called a window.")

[CORR Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/ea68d7a3796040bf9adb352e0756650e.html "Returns the correlation coefficient of a set of number pairs.") :arrow_upper_right:

