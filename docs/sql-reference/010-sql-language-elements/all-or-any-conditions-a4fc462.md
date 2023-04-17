<!-- loioa4fc462a84f210159d46aaed4b46192c -->

# ALL or ANY Conditions

Use ALL or ANY conditions in subqueries in search conditions.



## Syntax

The syntax for ALL conditions is as follows, where *<compare\>* is a comparison operator:

```
<expression> <compare> ALL ( <subquery> )
```

The syntax for ANY conditions is as follows, where *<compare\>* is a comparison operator:

```
<expression> <compare> ANY ( <subquery> )
```

For example, an ANY condition with an equality operator is TRUE if *<expression\>* is equal to any of the values in the result of the subquery, and FALSE if the expression is not NULL and does not equal any of the columns of the subquery:

```
<expression> = ANY ( <subquery> )
```

The ANY condition is UNKNOWN if *<expression\>* is the NULL value, unless the result of the subquery has no rows, in which case the condition is always FALSE.

You can use the keyword SOME instead of ANY.



<a name="loioa4fc462a84f210159d46aaed4b46192c__iq_refbb_83"/>

## Restrictions

If there is more than one expression on either side of a quantified comparison predicate, then an error message is returned. For example:

```
Subquery allowed only one select list item
```

Queries of this type can always be expressed in terms of IN subqueries or scalar subqueries using MIN and MAX set functions.



<a name="loioa4fc462a84f210159d46aaed4b46192c__iq_refbb_84"/>

## Compatibility

ANY and ALL subqueries are compatible between SAP Adaptive Server Enterprise and data lake Relational Engine. Only data lake Relational Engine supports SOME as a synonym for ANY.

