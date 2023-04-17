<!-- loioa4f6a6f484f210159ba7ba73f96538c6 -->

# CASE Expressions in Data Lake Relational Engine

The CASE expression provides conditional SQL expressions.



You can use case expressions anywhere you can use an expression. The syntax of the CASE expression is as follows:

```
CASE <expression>
WHEN <expression> THEN <expression> [, …]
[ ELSE <expression> ] END
```

You cannot use a subquery as a value expression in a CASE statement.

If the expression following the CASE statement is equal to the expression following the WHEN statement, then the expression following the THEN statement is returned. Otherwise, the expression following the ELSE statement is returned, if it exists.

For example, the following code uses a case expression as the second clause in a SELECT statement:

```
SELECT ID,
  (CASE name
  WHEN 'Tee Shirt' THEN 'Shirt'
  WHEN 'Sweatshirt' THEN 'Shirt'
  WHEN 'Baseball Cap' THEN 'Hat'
  ELSE 'Unknown'
  END) as Type
FROM "GROUPO".Products;
```

An alternative syntax is:

```
CASE
WHEN <search-condition> THEN <expression> [, …]
[ ELSE <expression> ] END
```

If the search condition following the WHEN statement is satisfied, then the expression following the THEN statement is returned. Otherwise, the expression following the ELSE statement is returned, if it exists.

The following example uses a case expression as the third clause of a SELECT statement to associate a string with a search condition:

```
SELECT ID, name,
  (CASE 
  WHEN name='Tee Shirt' THEN 'Sale'
  WHEN quantity >= 50  THEN 'Big Sale'
  ELSE 'Regular price'
  END) as Type
FROM "GROUPO".Products;
```

**Related Information**  


[NULLIF Function \[Miscellaneous\] for Data Lake Relational Engine](../050-system-sql-functions/nullif-function-miscellaneous-for-data-lake-relational-engine-a569fd1.md "Provides an abbreviated CASE expression by comparing expressions.")

[NULLIF Function for Abbreviated CASE Expressions in Data Lake Relational Engine](nullif-function-for-abbreviated-case-expressions-in-data-lake-relational-engine-a4f7256.md "The NULLIF function provides a way to write some CASE statements in short form.")

