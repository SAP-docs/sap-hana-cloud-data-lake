<!-- loioa65941ca84f210159194c9d97b112a8c -->

# SUBQUERY\_PLACEMENT\_PREFERENCE Option for Data Lake Relational Engine

Controls the placement of correlated subquery predicate operators within a query plan.



> ### Restriction:  
> This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa65941ca84f210159194c9d97b112a8c__iq_refso_970"/>

## Default

0



<a name="loioa65941ca84f210159194c9d97b112a8c__iq_refso_972"/>

## Remarks

For correlated subquery operators within a query, the optimizer may have a choice of several different valid locations within that query’s plan.

