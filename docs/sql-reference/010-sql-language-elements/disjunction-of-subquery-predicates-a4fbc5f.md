<!-- loioa4fbc5f084f21015b5b6e45c408e8c2b -->

# Disjunction of Subquery Predicates

The SQL89 standard allows for several forms of subquery predicates.



Each subquery can appear within the WHERE or HAVING clause with other predicates, and can be combined using the AND or OR operators. Data lake Relational Engine supports these subqueries, which can be correlated \(contain references to a table that appears in the outer query and cannot be evaluated independently\) and uncorrelated \(do not contain references to remote tables\).

The forms of subquery predicates include:

-   Unquantified comparison predicates:

    ```
    <scalar-expression> <comparison-operator> <subquery>
    ```

    The comparison operator is =, <\>, \>, \>=, <, or <=.

    Unquantified comparison subqueries return exactly one value. If the subquery returns more than one value, then an error message appears. This type of query is also called a scalar subquery predicate.

-   IN predicates:

    ```
    <scalar-expression> [NOT] IN <subquery>
    ```

    The IN subquery predicate returns a list of values or a single value. This type is also called a quantified subquery predicate.

-   Existence predicates:

    ```
    [NOT] EXISTS <subquery>
    ```

    The EXISTS predicate represents the existence of the subquery. The expression EXISTS <subquery\> evaluates to true only if the subquery result is not empty. The EXISTS predicate does not compare results with any column or expressions in the outer query block, and is typically used with correlated subqueries.

-   Quantified comparison predicates:

    ```
    <scalar-expression> <comparison-operator> [ANY | ALL] <subquery>
    ```

    A quantified comparison predicate compares one or a collection of values returned from a subquery.


The types of queries you can run include:

-   Disjunction of uncorrelated scalar subqueries or IN subqueries that cannot be executed vertically within the WHERE or HAVING clause.
-   Disjunction of correlated or uncorrelated EXISTS subqueries within the WHERE or HAVING clause.
-   Disjunction of arbitrary correlated or uncorrelated scalar subqueries, IN or EXISTS subqueries, or quantified comparison subqueries within the WHERE or HAVING clause.
-   Arbitrary uncorrelated or correlated subquery predicates combined with AND/OR \(conjunct/disjunct\) and simple predicates or subquery predicates.
-   Conjunction or disjunction of subquery predicates on top of a view/derived table.
-   Disjunction of subquery predicates in UPDATE, DELETE, and SELECT INTO statements.

The SUBQUERY\_CACHING\_PREFERENCE option lets experienced DBAs choose which subquery caching method to use.



<a name="loioa4fbc5f084f21015b5b6e45c408e8c2b__iq_refbb_81"/>

## Examples



### Example 1

Disjunction of uncorrelated EXISTS and IN subqueries:

```
SELECT COUNT(*)
FROM supplier 
WHERE s_suppkey IN (SELECT MAX(l_suppkey) 
            FROM lineitem 
            GROUP BY l_linenumber) 
OR EXISTS (SELECT p_brand 
      FROM part 
      WHERE p_brand = 'Brand#43');
```



### Example 2

Disjunction of uncorrelated EXISTS subqueries:

```
SELECT COUNT(*)
FROM supplier 
WHERE EXISTS (SELECT l_suppkey 
        FROM lineitem 
        WHERE l_suppkey = 12345) 
OR EXISTS   (SELECT p_brand 
        FROM part 
        WHERE p_brand = 'Brand#43');
```



### Example 3

Disjunction of uncorrelated scalar or IN subquery predicates:

```
SELECT COUNT(*) 
FROM supplier 
WHERE s_acctbal*10 > (SELECT MAX(o_totalprice) 
             FROM orders 
             WHERE o_custkey = 12345)
OR substring(s_name, 1, 6) IN (SELECT c_name 
                  FROM Customers 
                  WHERE c_nationkey = 10);
```



### Example 4

Disjunction of correlated/uncorrelated quantified comparison subqueries:

```
SELECT COUNT(*) 
FROM lineitem 
WHERE l_suppkey > ANY (SELECT MAX(s_suppkey)
              FROM supplier 
              WHERE s_acctbal >100 
              GROUP BY s_nationkey) 
OR l_partkey >= ANY (SELECT MAX(p_partkey) 
            FROM part 
            GROUP BY p_mfgr);
```



### Example 5

Disjunction of any correlated subquery predicates:

```
SELECT COUNT(*) 
FROM supplier S 
WHERE EXISTS (SELECT l_suppkey 
        FROM lineitem 
        WHERE l_suppkey = S.s_suppkey) 

OR EXISTS (SELECT p_brand FROM part 
      WHERE p_brand = 'Brand#43' 
       AND p_partkey > S.s_suppkey);
```



### Example 6

Before support for disjunction of subqueries, users were required to write queries in two parts, and then use UNION to merge the final results.

The following query illustrates a merged query that gets the same results as the example for disjunction of any correlated subquery predicates:

```
SELECT COUNT(*)
FROM (SELECT s_suppkey FROM supplier S
   WHERE EXISTS (SELECT l_suppkey
           FROM lineitem
           WHERE l_suppkey = S.s_suppkey)
UNION 

SELECT s_suppkey
FROM supplier S
WHERE EXISTS (SELECT p_brand
        FROM part
        WHERE p_brand = 'Brand#43'
         AND p_partkey > S.s_suppkey)) as UD;
```

Performance of the merged query is suboptimal because it scans the supplier table twice and then merges the results from each UNION to return the final result.

