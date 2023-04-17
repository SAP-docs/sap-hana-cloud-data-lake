<!-- loioa4fdf19184f21015b41eb698aaa28a51 -->

# IN Conditions

Use IN conditions in subqueries to reduce the need to use multiple OR conditions:



The syntax for `IN` conditions is:

```
{ <expression> [ NOT ] IN ( <subquery> )
  | <expression> [ NOT ] IN ( <expression> )
  | <expression> [ NOT ] IN ( <value-expr1> , <value-expr2>
  [ , <value-expr3> ] … ) }
```

Without the `NOT` keyword, the `IN` condition is TRUE if *<expression\>* equals any of the listed values, UNKNOWN if *<expression\>* is the NULL value, and FALSE otherwise. The `NOT` keyword reverses the meaning of the condition but leaves UNKNOWN unchanged.

The maximum number of values allowed in an `IN` condition list is 250,000.



<a name="loioa4fdf19184f21015b41eb698aaa28a51__iq_refbb_99"/>

## Compatibility

`IN` conditions are compatible between SAP Adaptive Server Enterprise and data lake Relational Engine.

