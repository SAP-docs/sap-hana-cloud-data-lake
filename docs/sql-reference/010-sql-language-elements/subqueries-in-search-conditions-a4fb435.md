<!-- loioa4fb435084f2101592cffd5b502c42fb -->

# Subqueries in Search Conditions

A subquery is a SELECT statement enclosed in parentheses. Such a SELECT statement must contain one and only one select list item.

A column can be compared to a subquery in a comparison condition \(for example, \>,<, or !=\) as long as the subquery returns no more than one row. If the subquery \(which must have one column\) returns one row, then the value of that row is compared to the expression. If a subquery returns no rows, then its value is NULL.

Subqueries that return exactly one column and any number of rows can be used in IN conditions, ANY conditions, ALL conditions, or EXISTS conditions. These conditions are discussed in the following sections.

Data lake Relational Engine supports UNION only in uncorrelated subquery predicates, not in scalar value subqueries, or correlated subquery predicates.

Subqueries cannot be used inside a CONTAINS or LIKE predicate.

Data lake Relational Engine does not support multiple subqueries in a single OR clause. For example, the following query has two subqueries joined by an OR:

```
CREATE VARIABLE @ln int;
SELECT @ln = 1;
SELECT COUNT(*) FROM lineitem WHERE 
l_shipdate IN (SELECT l_shipdate FROM lineitem WHERE l_orderkey IN (2,4,6))OR 
l_shipdate IN (SELECT l_shipdate FROM lineitem WHERE l_orderkey IN (1,3,5))OR 
l_linenumber = @ln;
```

Similar subqueries joined by AND and BETWEEN are allowed.

**Related Information**  


[Expressions in Data Lake Relational Engine](expressions-in-data-lake-relational-engine-a4ee102.md "Expressions are formed from different kinds of elements, such as constants, column names, SQL operators, and subqueries.")

[NULL Value in Data Lake Relational Engine](null-value-in-data-lake-relational-engine-a5107a2.md "Use NULL to specify a value that is unknown, missing, or not applicable.")

[Search Conditions in Data Lake Relational Engine](search-conditions-in-data-lake-relational-engine-a4fa3d9.md "Conditions are used to choose a subset of the rows from a table, or in a control statement such as an IF statement to determine control of flow.")

[Strings in Data Lake Relational Engine](strings-in-data-lake-relational-engine-a4ed4ed.md "Strings are either literal strings, or expressions with CHAR or VARCHAR data types.")

[Three-Valued Logic](three-valued-logic-a501bc6.md "The AND, OR, NOT, and IS logical operators of SQL work in three-valued logic.")

[SQL Operators in Data Lake Relational Engine](sql-operators-in-data-lake-relational-engine-a4f0a69.md "These topics describe the arithmetic, string, and bitwise operators available in data lake Relational Engine.")

[Comparison Conditions](comparison-conditions-a4fabf2.md "Comparison conditions in search conditions use a comparison operator.")

