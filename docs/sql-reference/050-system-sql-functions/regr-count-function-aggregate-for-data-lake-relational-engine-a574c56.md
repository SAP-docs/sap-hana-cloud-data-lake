<!-- loioa574c56884f21015b7b6f6bde76a2e6a -->

# REGR\_COUNT Function \[Aggregate\] for Data Lake Relational Engine

Returns an integer that represents the number of non-NULL number pairs used to fit the regression line.



 Syntax 1
 :   ```
REGR_COUNT( <dependent-expression>, <independent-expression> )
```

  Syntax 2
 :   ```
REGR_COUNT( <dependent-expression>, <independent-expression> )
OVER ( <window-spec> )
```

 

<a name="loioa574c56884f21015b7b6f6bde76a2e6a__REGR_COUNT_parm1"/>

## Parameters

 *<dependent-expression\>*
 :   The variable that is affected by the independent variable.

  *<independent-expression\>*
 :   The variable that influences the outcome.

  *<window-spec\>*
 :   Specified when using this function as a window function.

 

<a name="loioa574c56884f21015b7b6f6bde76a2e6a__REGR_COUNT_returns1"/>

## Returns

INTEGER



<a name="loioa574c56884f21015b7b6f6bde76a2e6a__REGR_COUNT_remarks1"/>

## Remarks

This function returns an UNSIGNED BIGINT as the result.

> ### Note:  
> ROLLUP and CUBE are not supported in the `GROUP BY` clause with Syntax 1. DISTINCT is not supported.

Syntax 2 – The *<window-spec\>* parameter represents usage as a window function in a `SELECT` statement. As such, you can specify elements of *<window-spec\>* either in the function syntax \(inline\), or with a `WINDOW` clause in the `SELECT` statement.



<a name="loioa574c56884f21015b7b6f6bde76a2e6a__REGR_COUNT_standards1"/>

## Standards and Compatibility

-   SQL – ISO/ANSI SQL compliant. SQL/OLAP feature T612.
-   SAP database products – compatible with SAP SQL Anywhere



<a name="loioa574c56884f21015b7b6f6bde76a2e6a__REGR_COUNT_example1"/>

## Example

The following example returns a value that indicates the number of non-NULL pairs that were used to fit the regression line:

```
SELECT REGR_COUNT( Salary, ( YEAR( NOW() ) - YEAR( BirthDate ) ) )FROM Employees;
```

This function returns the value 75.

**Related Information**  


[Windowing Aggregate Function Usage in Data Lake Relational Engine](windowing-aggregate-function-usage-in-data-lake-relational-engine-a527f35.md "A major feature of the ISO/ANSI SQL extensions for OLAP is a construct called a window.")

[REGR_COUNT Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/6ae6fc4e7e5e41489f2f3481cc6f8a3d.html "Returns an integer that represents the number of non-NULL number pairs used to fit the regression line.") :arrow_upper_right:

