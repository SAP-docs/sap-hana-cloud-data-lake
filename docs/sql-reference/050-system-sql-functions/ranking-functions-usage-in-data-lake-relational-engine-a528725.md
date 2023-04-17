<!-- loioa528725384f21015a9cab9ae54f06e9d -->

# Ranking Functions Usage in Data Lake Relational Engine

The OLAP ranking functions let application developers compose single-statement SQL queries that answer questions such as "Name the top 10 products shipped this year by total sales," or "Give the top 5% of salespeople who sold orders to at least 15 different companies."



These functions include the ranking functions, RANK\(\), DENSE\_RANK\(\), PERCENT\_RANK\(\), ROW\_NUMBER\(\), and NTILE\(\).

Rank analytical functions rank items in a group, compute distribution, and divide a result set into a number of groupings. The rank analytical functions, RANK\(\), DENSE\_RANK\(\), PERCENT\_RANK\(\), ROW\_NUMBER\(\), and NTILE\(\) all require an OVER \(ORDER BY\) clause. For example:

```
RANK() OVER ( [PARTITION BY] ORDER BY <expression> 
                                                [ ASC | DESC ] )
```

The ORDER BY clause specifies the parameter on which ranking is performed and the order in which the rows are sorted in each group. This ORDER BY clause is used only within the OVER clause and is not an ORDER BY for SELECT. No aggregation functions in the rank query ROW are allowed to specify DISTINCT.

> ### Note:  
> The OVER \(ORDER\_BY\) clause of the ROW\_NUMBER\(\) function cannot contain a ROWS or RANGE clause.

The OVER clause indicates that the function operates on a query result set. The result set is the rows that are returned after the FROM, WHERE, GROUP BY, and HAVING clauses have all been evaluated. The OVER clause defines the data set of the rows to include in the computation of the rank analytical function.

The value *<expression\>* is a sort specification that can be any valid expression involving a column reference, aggregates, or expressions invoking these items.

The ASC or DESC parameter specifies the ordering sequence as ascending or descending. Ascending order is the default.

Rank analytical functions are only allowed in the select list of a SELECT or INSERT statement or in the ORDER BY clause of the SELECT statement. Rank functions can be in a view or a union. You cannot use rank functions in a subquery, a HAVING clause, or in the select list of an UPDATE or DELETE statement. More than one rank analytical function is allowed per query in data lake Relational Engine.

