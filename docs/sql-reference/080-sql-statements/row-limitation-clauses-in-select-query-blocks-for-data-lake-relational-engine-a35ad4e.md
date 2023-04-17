<!-- loioa35ad4ee84f21015a4e0f12b17c1b13c -->

# Row Limitation Clauses in SELECT Query Blocks for Data Lake Relational Engine 

The FIRST, TOP, and LIMIT clauses allow you to return a subset of the rows that satisfy the WHERE clause. The FIRST, TOP, and LIMIT clauses can be used within any SELECT query block that includes an ORDER BY clause. FIRST, TOP, and LIMIT can only be used in the top query block in a statement.



The FIRST, TOP, and LIMIT clauses are row-limitation clauses and they have the following syntax:

```
<row-limitation-option-1> ::=
    FIRST | TOP { ALL | <limit-expression> } [ START AT <startat-expression> ]
```

```
<row-limitation-option-2> ::=
    LIMIT { [ <offset-expression>, ] <limit-expression> | <limit-expression>
    OFFSET <offset-expression> }
```

```
limit-expression ::= <simple-expression>
```

```
startat-expression ::= <simple-expression>
```

```
offset-expression ::= <simple-expression>
```

```
<simple-expression>
```

Only one row limitation clause can be specified for a SELECT clause. When specifying these clauses, an ORDER BY clause is required to order the rows in a meaningful manner.



## Parameters

*<row-limitation-option-1\>*
:   This type of clause can be used in SELECT query blocks only. The TOP and START AT arguments can be simple arithmetic expressions over host variables, integer constants, or integer variables. The TOP argument must evaluate to a value greater than or equal to 0. The START AT argument must evaluate to a value greater than 0. If ::= integer | variable | \( simple-expression \) | \( simple-expression \{ + | - | \* \} simple-expression \)*<startat-expression\>* is not specified the default is 1.

    The expression `limit-expression + startat-expression -1` ::= must evaluate to a value less than 9223372036854775807 = 2^64-1. If the argument of TOP is ALL, all rows starting at startat-expression are returned.

    The `TOP limit-expression START AT startat-expression` clause is equivalent to `LIMIT (startat-expression-1)`, `limit-expression` or `LIMIT limit-expression OFFSET (startat-expression-1)`.

*<row-limitation-option-2\>*
:   This type of clause can be used in SELECT query blocks only. The LIMIT and OFFSET arguments can be simple arithmetic expressions over host variables, integer constants, or integer variables. The LIMIT argument must evaluate to a value greater than or equal to 0. The OFFSET argument must evaluate to a value greater than or equal to 0. If offset-expression is not specified, the default is 0. The expression `limit-expression + offset-expression` must evaluate to a value less than 9223372036854775807 = 2^64-1.

The row-limitation clause `LIMIT offset-expression, limit-expression` is equivalent to `LIMIT limit-expression OFFSET offset-expression`. Both of these constructs are equivalent to `TOP limit-expression START AT (offset-expression + 1)`.

The LIMIT keyword is disabled by default. Use the reserved\_keywords option to enable the LIMIT keyword.

**Related Information**  


[SELECT Statement for Data Lake Relational Engine](select-statement-for-data-lake-relational-engine-a624e72.md "Retrieves information from the database.")

[GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[GRANT Object-Level Privilege Statement for Data Lake Relational Engine](grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md "Grants database object-level privileges on individual objects and schemas to a user or role.")

