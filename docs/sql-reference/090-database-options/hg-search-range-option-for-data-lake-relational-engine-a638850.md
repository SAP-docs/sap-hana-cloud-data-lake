<!-- loioa638850284f21015a1a9993e5cc4b710 -->

# HG\_SEARCH\_RANGE Option for Data Lake Relational Engine

Specifies the maximum number of Btree pages used in evaluating a range predicate in the HG index.



> ### Restriction:  
> This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa638850284f21015a1a9993e5cc4b710__iq_refso_592"/>

## Default

10



<a name="loioa638850284f21015a1a9993e5cc4b710__iq_refso_594"/>

## Remarks

This option effectively controls the amount of time the optimizer spends searching for the best index to use for a range predicate.

The default setting of this option is appropriate for most queries.

