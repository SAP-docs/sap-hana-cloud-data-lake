<!-- loioa502c2bf84f2101596b7b37351e50040 -->

# User-Supplied Condition Selectivity

The simplest form of condition hint is to supply a selectivity value to be used instead of the value the optimizer would have computed.

Selectivity hints are supplied within the text of the query by wrapping the condition within parentheses. Then within the parentheses, after the condition, you add a comma and a numeric value to be used as the selectivity.

This selectivity value is expressed as a percentage of the table’s rows, which satisfy the condition. Possible numeric values for selectivity thus range from 100.0 to 0.0.

> ### Note:  
> In query plans, selectivity is expressed as a fraction instead of as a percentage; so a user-supplied selectivity of 35.5 appears in that query’s plan as a selectivity of 0.355000.



<a name="loioa502c2bf84f2101596b7b37351e50040__iq_refbb_113"/>

## Examples

-   The following query provides an estimate that one and one half percent of the ship\_date values are earlier than 1994/06/30:

    ```
    SELECT  ShipDate
    FROM  SalesOrderItems
    WHERE ( ShipDate < '2001/06/30', 1.5 )
    ORDER BY ShipDate DESC
    ```

-   The following query estimates that half a percent of the rows satisfy the condition:

    ```
    SELECT *
    FROM Customers c, SalesOrders o
    WHERE (o.SalesRepresentative > 1000.0, 0.5) 
      AND c.ID = o.customerID
    ```


Fractional percentages enable more precise user estimates to be specified and can be particularly important for large tables.



<a name="loioa502c2bf84f2101596b7b37351e50040__iq_refbb_114"/>

## Compatibility

SAP SQL Anywhere supports user-supplied selectivity estimates.

SAP Adaptive Server Enterprise does not support user-supplied selectivity estimates.

**Related Information**  


[Selectivity Hints](selectivity-hints-a503d71.md "The first hint type that can appear within a hint string is a selectivity hint. A selectivity hint is identified by a hint type identifier of either “S” or “s”.")

