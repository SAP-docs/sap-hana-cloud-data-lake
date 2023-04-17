<!-- loioa63494cd84f210159d72d59e38117625 -->

# DEFAULT\_LIKE\_RANGE\_SELECTIVITY\_PPM Option for Data Lake Relational Engine

Provides default selectivity estimates \(in parts per million\) to the optimizer for leading constant LIKE predicates.



> ### Restriction:  
> This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa63494cd84f210159d72d59e38117625__iq_refso_503"/>

## Default

150,000



<a name="loioa63494cd84f210159d72d59e38117625__iq_refso_505"/>

## Remarks

DEFAULT\_LIKE\_RANGE\_SELECTIVITY\_PPM sets the default selectivity for LIKE predicates, of the form LIKE '*<string%\>*' where the match string is a set of constant characters followed by a single wildcard character \(%\). The optimizer relies on this option when other selectivity information is not available.

If the column has a 1- or 2- or 3-byte FP index, the optimizer can get exact information and does not need to use this value.

You can also specify selectivity \(user-supplied condition hints\) in the query.

**Related Information**  


[User-Supplied Condition Hints](../010-sql-language-elements/user-supplied-condition-hints-a5023f4.md "The selectivity of a condition is the fraction of the table’s rows that satisfy that condition.")

[DEFAULT\_LIKE\_MATCH\_SELECTIVITY\_PPM Option for Data Lake Relational Engine](default-like-match-selectivity-ppm-option-for-data-lake-relational-engine-a634664.md "Provides default selectivity estimates (in parts per million) to the optimizer for most LIKE predicates.")

[FP\_LOOKUP\_SIZE Optionfor Data Lake Relational Engine](fp-lookup-size-optionfor-data-lake-relational-engine-a63673f.md "Specifies the number of lookup pages and cache memory allocated for Lookup FP indexes in data lake Relational Engine databases.")

