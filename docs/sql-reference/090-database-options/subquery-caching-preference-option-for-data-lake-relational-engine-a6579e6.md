<!-- loioa6579e6884f21015b85e9256bf3ac5ec -->

# SUBQUERY\_CACHING\_PREFERENCE Option for Data Lake Relational Engine

Controls which algorithm to use for processing correlated subquery predicates.



> ### Restriction:  
> This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa6579e6884f21015b85e9256bf3ac5ec__iq_refso_957"/>

## Default

0



<a name="loioa6579e6884f21015b85e9256bf3ac5ec__iq_refso_959"/>

## Remarks

For correlated subquery predicates, the optimizer offers a choice of caching outer references and subquery results that reduces subquery execution costs.

SUBQUERY\_CACHING\_PREFERENCE does not apply to IN subqueries.

**Related Information**  


[IN\_SUBQUERY\_PREFERENCE Option for Data Lake Relational Engine](in-subquery-preference-option-for-data-lake-relational-engine-a63a081.md "Controls the choice of algorithms for processing an IN subquery.")

