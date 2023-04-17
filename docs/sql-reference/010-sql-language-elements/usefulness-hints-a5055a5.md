<!-- loioa5055a5684f21015995cabd277d60373 -->

# Usefulness Hints

The final supported hint type is the usefulness hint, which is identified by a hint type identifier of either “U” or “u”.

The value for a usefulness hint can be any numeric value between 0.0 and 10.0. Within the optimizer a usefulness value is computed for every condition, and the usefulness value is then used to determine the order of evaluation among the set of conditions to be evaluated within the same phase of execution. The higher the usefulness value, the earlier it appears in the order of evaluation. Supplying a usefulness hint lets users place a condition at a particular point within the order of evaluation, but it cannot change the execution phase within which the condition is evaluated.



<a name="loioa5055a5684f21015995cabd277d60373__iq_refbb_118"/>

## Example

The following example shows a condition hint string that indicates that the condition should be moved into the “Delayed” phase of execution, and that its usefulness should be set to 3.25 within that “Delayed” phase:

```
SELECT *
FROM Customers c, SalesOrders o
WHERE (co.SalesRepresentative > 10000.0, 'U: 3.25,  E: D')
AND c.id = o.CustomerID
```



<a name="loioa5055a5684f21015995cabd277d60373__iq_refbb_119"/>

## Compatibility

SAP SQL Anywhere does not support user-supplied condition hint strings.

SAP Adaptive Server Enterprise does not support user-supplied condition hint strings.

