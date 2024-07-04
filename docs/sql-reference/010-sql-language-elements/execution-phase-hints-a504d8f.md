<!-- loioa504d8f884f21015a156e4bf2c0253dc -->

# Execution Phase Hints

The third supported hint type is the execution phase hint, which is identified with a hint type identifier of either "E" or "e".

Within the data lake Relational Engine query engine, there are four distinct phases of execution where conditions can be evaluated.

By default, the optimizer chooses to evaluate each condition within the earliest phase of execution where all the information needed to evaluate that condition is available. Every condition, therefore, has a default execution phase where it is evaluated.

Because no condition can be evaluated before the information it needs is available, the execution phase hint can only be used to delay the execution of a condition to a phase after its default phase. It cannot be used to force a condition to be evaluated within any phase earlier than its default phase.

The four phases of condition execution, from earliest to latest, are as follows:

-   Invariant – a condition that refers to only one column \(or two columns from the same table\) and that can be evaluated using an index is generally referred to as a simple invariant condition. Simple invariant conditions are normally evaluated early within the optimization process. This means that the number of rows satisfying all of those invariant conditions is available to guide the optimizer’s decisions on the best join order and join algorithms to use. Because this is the earliest phase of execution, a user can never force a condition into this phase, but conditions can be forced out of this phase into later phases
-   Delayed – some conditions cannot be evaluated until some other part of a query has been executed. These delayed conditions are evaluated once when the query node to which they are attached is first fetched. These conditions fall into two categories: uncorrelated subquery conditions, and IN or PROBABLY\_IN pushdown join conditions created by the optimizer.
-   Bound – some conditions require multiple evaluations. These conditions generally fall into two categories: conditions containing outer references within a correlated subquery, and pushdown equality join conditions created by the optimizer. The outer reference conditions, for example, are re-evaluated each time the outer reference value changes during the query's execution.
-   Horizontal – some conditions, such as those that contain more than two columns from a table, can only be evaluated one row at a time, rather than by using an index.

An execution phase hint accepts a value that identifies in which execution phase the user wants the condition to be evaluated. Each value is a case-insensitive single character:

-   D – Delayed
-   B – Bound
-   H – Horizontal



<a name="loioa504d8f884f21015a156e4bf2c0253dc__iq_refbb_117"/>

## Examples

The following example shows a condition hint string that indicates that the condition should be moved into the “Delayed” phase of execution, and it indicates that if possible the condition should be evaluated using an HG index:

```
SELECT *
FROM Customers c, SalesOrders o
WHERE (o.SalesRepresentative > 10000.0, 'E:D, I:2')
  AND c.id = o.CustomerID
```

