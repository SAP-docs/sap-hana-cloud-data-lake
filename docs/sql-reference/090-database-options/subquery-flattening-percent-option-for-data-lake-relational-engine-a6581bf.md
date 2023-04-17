<!-- loioa6581bf484f21015b11ee6c2d9aa56be -->

# SUBQUERY\_FLATTENING\_PERCENT Option for Data Lake Relational Engine

Allows the user to change the threshold at which the optimizer decides to transform scalar subqueries into joins.



> ### Restriction:  
> This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa6581bf484f21015b11ee6c2d9aa56be__iq_refso_961"/>

## Default

100



<a name="loioa6581bf484f21015b11ee6c2d9aa56be__iq_refso_963"/>

## Remarks

If you set SUBUERY\_FLATTENING\_PERCENT to a non-default value, every scalar subquery predicate in the query is affected; this option cannot be used selectively for one scalar subquery predicate in a query.

The data lake Relational Engine query optimizer can convert a correlated scalar subquery into an equivalent join operation to improve query performance. The SUBUERY\_FLATTENING\_PERCENT option allows the user to adjust the threshold at which this optimization occurs.

SUBUERY\_FLATTENING\_PERCENT represents a percent of estimated inner distinct values to estimated outer distinct values in a scalar subquery. As the estimated percent approaches 100 percent, the cost of evaluating the subquery as a join is likely to be smaller than using individual index probes. The value may be set larger than 100 percent, since the estimated inners are not guaranteed to be less than estimated outers.

**Related Information**  


[SUBQUERY\_FLATTENING\_PREFERENCE Option for Data Lake Relational Engine](subquery-flattening-preference-option-for-data-lake-relational-engine-a658c06.md "Allows a user to override the decisions of the optimizer when transforming (flattening) scalar or EXISTS subqueries into joins.")

