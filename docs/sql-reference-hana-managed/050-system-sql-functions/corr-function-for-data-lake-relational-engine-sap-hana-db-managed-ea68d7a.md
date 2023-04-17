<!-- loioea68d7a3796040bf9adb352e0756650e -->

# CORR Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

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

 

<a name="loioea68d7a3796040bf9adb352e0756650e__section_cm2_4ql_srb"/>

## Parameters

 *<dependent-expression\>*
 :   The variable that is affected by the *<independent-expression\>*.

  *<independent-expression\>*
 :   The variable that influences the outcome.

  *<window-spec\>*
 :   Specified when using this function as a window function.

 

<a name="loioea68d7a3796040bf9adb352e0756650e__section_brv_4ql_srb"/>

## Returns

DOUBLE



<a name="loioea68d7a3796040bf9adb352e0756650e__section_p3k_pql_srb"/>

## Remarks

The `CORR` function converts its arguments to DOUBLE, performs the computation in double-precision floating-point, and returns a DOUBLE as the result. If applied to an empty set, then CORR returns NULL.

Both *<dependent-expression\>* and *<independent-expression\>* are numeric. The function is applied to the set of \(*<dependent-expression\>*, *<independent-expression\>*\) after eliminating the pairs for which either *<dependent-expression\>* or *<independent-expression\>* is NULL. The following computation is made, where *<x\>* represents the *<dependent-expression\>* and *<y\>* represents the *<independent-expression\>*:

```
COVAR_POP (y, x) / (STDDEV_POP (x) * STDDEV_POP (y))
```

> ### Note:  
> ROLLUP and CUBE are not supported in the GROUP BY clause with Syntax 1.

Syntax 2 – The *<window-spec\>* parameter represents usage as a window function in a `SELECT` statement. As such, you can specify elements of *<window-spec\>* either in the function syntax \(inline\), or with a `WINDOW` clause in the `SELECT` statement.



<a name="loioea68d7a3796040bf9adb352e0756650e__section_ekn_qql_srb"/>

## Standards and Compatibility

-   SQL – ISO/ANSI SQL compliant. SQL foundation feature outside of core SQL.



<a name="loioea68d7a3796040bf9adb352e0756650e__section_ddv_rql_srb"/>

## Example

The following example performs a correlation to discover whether age is associated with income level. This function returns the value 0.440227:

```
SELECT CORR( Salary, ( YEAR( NOW( ) ) - YEAR( BirthDate ) ) ) FROM Employees;
```

**Related Information**  


[WINDOW Clause for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/window-clause-for-data-lake-relational-engine-sap-hana-db-managed-c83b61b.md "Defines all or part of a window for use with window functions such as AVG and RANK in a SELECT statement.")

[CORR Function [Aggregate] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a53fefea84f21015a7ac9e118cc9795c.html "Returns the correlation coefficient of a set of number pairs.") :arrow_upper_right:
