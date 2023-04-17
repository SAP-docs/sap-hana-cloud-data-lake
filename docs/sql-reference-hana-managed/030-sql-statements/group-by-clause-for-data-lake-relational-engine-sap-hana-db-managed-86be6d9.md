<!-- loio86be6d9a901f4b1ca1977a88cc39b545 -->

# GROUP BY Clause for Data Lake Relational Engine \(SAP HANA DB-Managed\)



```
GROUP BY
| <group-by-term>, ... 
| <simple-group-by-term>, ...  WITH ROLLUP
| <simple-group-by-term>, ... WITH CUBE
| GROUPING SETS ( <group-by-term>, ... )
```

```
<group-by-term> :
<simple-group-by-term>
| ( <simple-group-by-term>, ... )
| ROLLUP ( <simple-group-by-term>, ... )
| CUBE ( <simple-group-by-term>, ... )
```

```
<simple-group-by-term> :
<expression>
| ( <expression> ) 
| ( )
```



<a name="loio86be6d9a901f4b1ca1977a88cc39b545__section_mzz_2jp_njb"/>

## Parameters

 GROUPING SETS clause
 :   The GROUPING SETS clause allows you to perform aggregate operations on multiple groupings from a single query specification. Each set specified in a GROUPING SET clause is equivalent to a GROUP BY clause.

    For example, the following two queries are equivalent:

    ```
    SELECT a, b, SUM( c ) FROM t 
    GROUP BY GROUPING SETS ( ( a, b ), ( a ), ( b ), ( ) );
    ```

    ```
    SELECT a, b, SUM( c ) FROM t 
      GROUP BY a, b 
    UNION ALL
    SELECT a, NULL, SUM( c ) FROM t 
      GROUP BY a 
    UNION ALL
    SELECT NULL, b, SUM( c ) FROM t 
      GROUP BY b 
    UNION ALL
    SELECT NULL, NULL, SUM( c ) FROM t;
    ```

    A grouping expression may be reflected in the result set as a NULL value, depending on the grouping in which the result row belongs. This may cause confusion over whether the NULL is the result of another grouping, or whether the NULL is the result of an actual NULL value in the underlying data. To distinguish between NULL values present in the input data and NULL values inserted by the grouping operator, use the GROUPING function.

    Specifying an empty set of parentheses \( \) in the GROUPING SETS clause returns a single row containing the overall aggregate.

  ROLLUP clause
 :   The ROLLUP clause is similar to the GROUPING SETS clause in that it can be used to specify multiple grouping specifications within a single query specification. A ROLLUP clause of *<n\>* *<simple-group-by-term\>*s generates *<n\>*+1 grouping sets, formed by starting with the empty parentheses, and then appending successive *<group-by-term\>*s from left to right.

    For example, the following two statements are equivalent:

    ```
    SELECT a, b, SUM( c ) FROM t 
    GROUP BY ROLLUP ( a, b );
    ```

    ```
    SELECT a, b, SUM( c ) FROM t 
    GROUP BY GROUPING SETS ( ( a, b ), a, ( ) );
    ```

    You can use a ROLLUP clause within a GROUPING SETS clause.

  CUBE clause
 :   The CUBE clause is similar to the ROLLUP and GROUPING SETS clauses in that it can be used to specify multiple grouping specifications within a single query specification. The CUBE clause is used to represent all possible combinations that can be made from the expressions listed in the CUBE clause.

    For example, the following two statements are equivalent:

    ```
    SELECT a, b, SUM( c ) FROM t 
    GROUP BY CUBE ( a, b, c );
    ```

    ```
    SELECT a, b, SUM( c ) FROM t 
    GROUP BY GROUPING SETS ( ( a, b, c ), ( a, b ), ( a, c ), 
     ( b, c ), a, b, c, () );
    ```

    You can use a CUBE clause within a GROUPING SETS clause.

  WITH ROLLUP clause
 :   This is an alternative syntax to the ROLLUP clause, and is provided for Transact-SQL compatibility.

  WITH CUBE clause
 :   This is an alternate syntax to the CUBE clause, and is provided for Transact-SQL compatibility.

 

<a name="loio86be6d9a901f4b1ca1977a88cc39b545__section_nzz_2jp_njb"/>

## Remarks

When using the GROUP BY clause, you can group by expressions \(with some limitations\), columns, alias names, or functions. The result of the query contains one row for each distinct value \(or set of values\) of each grouping set.

The empty GROUP BY list, \(\), signifies the treatment of the entire input as a single group. For example, the following two statements are equivalent:

```
SELECT COUNT(), SUM(Salary) FROM GROUPO.Employees;
```

```
SELECT COUNT(), SUM(Salary) FROM GROUPO.Employees GROUP BY ();
```



<a name="loio86be6d9a901f4b1ca1977a88cc39b545__section_pzz_2jp_njb"/>

## Standards

 ANSI/ISO SQL Standard
 :   Core Feature. GROUPING SETS, GROUP BY \(\), ROLLUP, and CUBE constitute portions of optional ANSI/ISO SQL Language Feature T431. The software doesn’t support optional ANSI/ISO SQL Language Feature T432, "Nested and concatenated GROUPING SETS".

    Extensions to the GROUP BY clause that aren’t in the standard include:

    -   WITH ROLLUP

    -   WITH CUBE

    -   the ability to specify arbitrary expressions as GROUP BY terms. In the ANSI/ISO SQL Standard, every GROUP BY term must be a column reference from an underlying table in the query's FROM clause.


 

The following example returns a result set showing the total number of orders, and then provides subtotals for the number of orders in each year \(2000 and 2001\).

```
SELECT YEAR( ORDERDATE) Year, QUARTER( ORDERDATE) Quarter, COUNT(*) ORDERSE
FROM GROUPO.SALESORDERS
GROUP BY ROLLUP ( YEAR, QUARTER )
ORDER BY YEAR, QUARTER;
```

Like the preceding ROLLUP operation example, the following CUBE query example returns a result set showing the total number of orders and provides subtotals for the number of orders in each year \(2000 and 2001\). Unlike ROLLUP, this query also gives subtotals for the number of orders in each quarter \(1, 2, 3, and 4\).

```
SELECT YEAR(ORDERDATE) YEAR, QUARTER( ORDERDATE) QUARTER, COUNT(*) ORDERS FROM GROUPO.SalesOrders
GROUP BY CUBE ( YEAR, QUARTER )
ORDER BY YEAR, QUARTER;
```

The following example returns a result set that gives subtotals for the number of orders in the years 2000 and 2001. The GROUPING SETS operation lets you select the columns to be subtotaled instead of returning all combinations of subtotals like the CUBE operation.

```
SELECT YEAR((ORDERDATE) YEAR, QUARTER( ORDERDATE) QUARTER, COUNT(*) ORDERS 
FROM GROUPO.SALESORDERS
GROUP BY GROUPING SETS ( ( YEAR, QUARTER ), ( YEAR ) )
ORDER BY YEAR, QUARTER;
```

