<!-- loioa636d40284f21015b7a0a8eb955eaf8b -->

# FP\_PREDICATE\_WORKUNIT\_PAGES Option for Data Lake Relational Engine

Specifies degree of parallelism used in the default index.



> ### Restriction:  
> This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa636d40284f21015b7a0a8eb955eaf8b__iq_refso_553"/>

## Default

200



<a name="loioa636d40284f21015b7a0a8eb955eaf8b__iq_refso_555"/>

## Remarks

The default index calculates some predicates such as SUM, RANGE, MIN, MAX and COUNT DISTINCT in parallel. FP\_PREDICATE\_WORKUNIT\_PAGES sets the degree of parallelism used by specifying the number of pages worked on by each thread.

