<!-- loioa3593ef084f2101587cccb33b61e47ac -->

# IS DISTINCT FROM Search Conditions

Use the IS DISTINCT FROM and IS NOT DISTINCT FROM search conditions as comparison operators.



## Syntax

<code><i class="varname">&lt;expression1&gt;</i> IS [ NOT ] DISTINCT FROM <i class="varname">&lt;expression2&gt;</i></code>



## Remarks

The IS DISTINCT FROM and IS NOT DISTINCT FROM search conditions are sargable and evaluate to TRUE or FALSE.

The IS NOT DISTINCT FROM search condition evaluates to TRUE if *<expression1\>* is equal to *<expression2\>*, or if both expressions are NULL. This is equivalent to a combination of two search conditions, as follows:

```
expression1 = expression2 OR ( expression1 IS NULL AND expression2 IS NULL )
```

The IS DISTINCT FROM syntax reverses the meaning. That is, IS DISTINCT FROM evaluates to TRUE if *<expression1\>* is not equal to *<expression2\>*, and at least one of the expressions is not NULL. This is equivalent to the following:

```
NOT( expression1 = expression2 OR ( expression1 IS NULL AND expression2 IS NULL ))
```



## Standards and Compatibility

SQL/2008
:   The IS \[NOT\] DISTINCT FROM predicate is defined in SQL/2008 standard. The IS DISTINCT FROM predicate is Feature T151, "DISTINCT predicate", of the SQL/2008 standard. The IS NOT DISTINCT FROM predicate is Feature T152, "DISTINCT predicate with negation", of the SQL/2008 standard.

