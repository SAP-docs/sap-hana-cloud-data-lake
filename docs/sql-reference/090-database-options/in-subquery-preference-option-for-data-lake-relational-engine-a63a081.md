<!-- loioa63a081184f21015bb298a8b5cf87cbe -->

# IN\_SUBQUERY\_PREFERENCE Option for Data Lake Relational Engine

Controls the choice of algorithms for processing an IN subquery.



<a name="loioa63a081184f21015bb298a8b5cf87cbe__section_rv2_mvs_swb"/>

## Usage

This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa63a081184f21015bb298a8b5cf87cbe__iq_refso_630"/>

## Default

0



<a name="loioa63a081184f21015bb298a8b5cf87cbe__iq_refso_632"/>

## Remarks

The IQ optimizer has a choice of several algorithms for processing IN subqueries. This option controls the optimizer's costing decision when choosing the algorithm to use. It does not override internal rules that determine whether an algorithm is legal within the query engine.

