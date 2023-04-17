<!-- loioa503d71784f21015aa539a161cd1eff1 -->

# Selectivity Hints

The first hint type that can appear within a hint string is a selectivity hint. A selectivity hint is identified by a hint type identifier of either “S” or “s”.

Like user-supplied selectivity estimates, the selectivity value is always expressed as a percentage of the table’s rows, which satisfy the condition.



The following example is exactly equivalent to the second user-supplied condition selectivity example:

```
SELECT *
FROM Customers c, SalesOrders o
WHERE (o.SalesRepresentative > 1000.0, 's: 0.5)
  AND c.ID = o.CustomerID
```

**Related Information**  


[User-Supplied Condition Selectivity](user-supplied-condition-selectivity-a502c2b.md "The simplest form of condition hint is to supply a selectivity value to be used instead of the value the optimizer would have computed.")

