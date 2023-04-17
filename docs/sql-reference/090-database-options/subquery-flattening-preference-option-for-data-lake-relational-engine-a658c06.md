<!-- loioa658c06a84f210158cf7e178e9518c2f -->

# SUBQUERY\_FLATTENING\_PREFERENCE Option for Data Lake Relational Engine

Allows a user to override the decisions of the optimizer when transforming \(flattening\) scalar or EXISTS subqueries into joins.



> ### Restriction:  
> This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa658c06a84f210158cf7e178e9518c2f__iq_refso_965"/>

## Default

0



<a name="loioa658c06a84f210158cf7e178e9518c2f__iq_refso_967"/>

## Remarks

The data lake Relational Engine optimizer may convert a correlated scalar subquery or an EXISTS or NOT EXISTS subquery into an equivalent join operation to improve query performance. This optimization is called subquery flattening. SUBQUERY\_FLATTENING\_PREFERENCE allows you to override the costing decision of the optimizer when choosing the algorithm to use.

