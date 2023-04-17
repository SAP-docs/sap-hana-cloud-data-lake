<!-- loioa4fcd13884f21015b8bcbbfb9ce583fe -->

# BETWEEN Conditions

Use `BETWEEN` conditions in subqueries to retrieve values within a range.



The syntax for `BETWEEN` conditions is as follows:

```
<expr> [ NOT ] BETWEEN <start-expr> AND <end-expr>
```

The `BETWEEN` condition can evaluate as TRUE, FALSE, or UNKNOWN. Without the `NOT` keyword, the condition evaluates as TRUE if *<expr\>* is between *<start-expr\>* and *<end-expr\>*. The `NOT` keyword reverses the meaning of the condition but leaves UNKNOWN unchanged.

The `BETWEEN` condition is equivalent to a combination of two inequalities:

```
<expr> >= <start-expr> AND <expr> <= <end-expr>
```

A `BETWEEN` predicate is of the form “A between B and C.” Either “B” or “C” or both “B” and “C” can be subqueries. “A” must be a value expression or column.



<a name="loioa4fcd13884f21015b8bcbbfb9ce583fe__iq_refbb_86"/>

## Compatibility

The `BETWEEN` condition is compatible between data lake Relational Engine and SAP Adaptive Server Enterprise.

