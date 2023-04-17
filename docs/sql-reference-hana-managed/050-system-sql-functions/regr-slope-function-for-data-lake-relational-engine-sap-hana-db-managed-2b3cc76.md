<!-- loio2b3cc76a26a04898952576a65be0272f -->

# REGR\_SLOPE Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Computes the slope of the linear regression line, fitted to non-NULL pairs.



 Syntax 1
 :   ```
REGR_SLOPE( <dependent-expression>, <independent-expression> )
```

  Syntax 2
 :   ```
REGR_SLOPE( <dependent-expression>, <independent-expression> )
OVER ( <window-spec> )
```

 

<a name="loio2b3cc76a26a04898952576a65be0272f__section_p15_xg5_vrb"/>

## Parameters

 *<dependent-expression\>*
 :   The variable that is affected by the independent variable.

  *<independent-expression\>*
 :   The variable that influences the outcome.

  *<window-spec\>*
 :   Specified when using this function as a window function.

 

<a name="loio2b3cc76a26a04898952576a65be0272f__section_vdk_yg5_vrb"/>

## Returns

DOUBLE



<a name="loio2b3cc76a26a04898952576a65be0272f__section_mrc_zg5_vrb"/>

## Remarks

This function converts its arguments to DOUBLE, performs the computation in double-precision floating-point, and returns a DOUBLE as the result. If applied to an empty set, then `REGR_SLOPE` returns NULL.

`REGR_SLOPE` is applied to the set of \(*<dependent-expression\>* and *<independent-expression\>*\) pairs after eliminating all pairs for which either *<dependent-expression\>* or *<independent-expression\>* is NULL. The function is computed simultaneously during a single pass through the data. After eliminating NULL values, the following computation is made, where *<y\>* represents the *<dependent-expression\>* and *<x\>* represents the *<independent-expression\>*:

```
COVAR_POP(x, y) / VAR_POP(y)
```

> ### Note:  
> ROLLUP and CUBE are not supported in the `GROUP BY` clause with Syntax 1. DISTINCT is not supported.

Syntax 2 – The *<window-spec\>* parameter represents usage as a window function in a `SELECT` statement. As such, you can specify elements of *<window-spec\>* either in the function syntax \(inline\), or with a `WINDOW` clause in the `SELECT` statement.



<a name="loio2b3cc76a26a04898952576a65be0272f__section_vkr_zg5_vrb"/>

## Standards and Compatibility

-   SQL – ISO/ANSI SQL compliant. SQL/OLAP feature T612.
-   SAP database products – compatible with SAP SQL Anywhere



<a name="loio2b3cc76a26a04898952576a65be0272f__section_vxd_1h5_vrb"/>

## Example

The following example returns the value 935.3429749445614:

```
SELECT REGR_SLOPE( Salary, ( YEAR( NOW() ) - YEAR( BirthDate ) ) )FROM Employees;
```

**Related Information**  


[WINDOW Clause for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/window-clause-for-data-lake-relational-engine-sap-hana-db-managed-c83b61b.md "Defines all or part of a window for use with window functions such as AVG and RANK in a SELECT statement.")

[REGR_SLOPE Function [Aggregate] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a57647a684f21015af3cb26e82eae9cd.html "Computes the slope of the linear regression line, fitted to non-NULL pairs.") :arrow_upper_right:

