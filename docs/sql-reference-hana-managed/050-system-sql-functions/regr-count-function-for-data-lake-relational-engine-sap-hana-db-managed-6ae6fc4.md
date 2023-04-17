<!-- loio6ae6fc4e7e5e41489f2f3481cc6f8a3d -->

# REGR\_COUNT Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

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

 

<a name="loio6ae6fc4e7e5e41489f2f3481cc6f8a3d__section_mgw_q35_vrb"/>

## Parameters

 *<dependent-expression\>*
 :   The variable that is affected by the independent variable.

  *<independent-expression\>*
 :   The variable that influences the outcome.

  *<window-spec\>*
 :   Specified when using this function as a window function.

 

<a name="loio6ae6fc4e7e5e41489f2f3481cc6f8a3d__section_hjl_r35_vrb"/>

## Returns

INTEGER



<a name="loio6ae6fc4e7e5e41489f2f3481cc6f8a3d__section_r2y_r35_vrb"/>

## Remarks

This function returns an UNSIGNED BIGINT as the result.

> ### Note:  
> ROLLUP and CUBE are not supported in the `GROUP BY` clause with Syntax 1. DISTINCT is not supported.

Syntax 2 – The *<window-spec\>* parameter represents usage as a window function in a `SELECT` statement. As such, you can specify elements of *<window-spec\>* either in the function syntax \(inline\), or with a `WINDOW` clause in the `SELECT` statement.



<a name="loio6ae6fc4e7e5e41489f2f3481cc6f8a3d__section_llm_s35_vrb"/>

## Standards and Compatibility

-   SQL – ISO/ANSI SQL compliant. SQL/OLAP feature T612.
-   SAP database products – compatible with SAP SQL Anywhere



<a name="loio6ae6fc4e7e5e41489f2f3481cc6f8a3d__section_ahv_s35_vrb"/>

## Example

The following example returns a value that indicates the number of non-NULL pairs that were used to fit the regression line:

```
SELECT REGR_COUNT( Salary, ( YEAR( NOW() ) - YEAR( BirthDate ) ) )FROM Employees;
```

This function returns the value 75.

**Related Information**  


[WINDOW Clause for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/window-clause-for-data-lake-relational-engine-sap-hana-db-managed-c83b61b.md "Defines all or part of a window for use with window functions such as AVG and RANK in a SELECT statement.")

[REGR_COUNT Function [Aggregate] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a574c56884f21015b7b6f6bde76a2e6a.html "Returns an integer that represents the number of non-NULL number pairs used to fit the regression line.") :arrow_upper_right:

