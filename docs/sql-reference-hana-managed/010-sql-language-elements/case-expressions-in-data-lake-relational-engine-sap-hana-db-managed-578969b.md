<!-- loio578969b704bd405591a2c71706494c26 -->

# CASE Expressions in Data Lake Relational Engine \(SAP HANA DB-Managed\)

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


[NULLIF Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../050-system-sql-functions/nullif-function-for-data-lake-relational-engine-sap-hana-db-managed-601a225.md "Provides an abbreviated CASE expression by comparing expressions.")

[NULLIF Function for Abbreviated CASE Expressions in Data Lake Relational Engine \(SAP HANA DB-Managed\)](nullif-function-for-abbreviated-case-expressions-in-data-lake-relational-engine-sap-han-317f04d.md "The NULLIF function provides a way to write some CASE statements in short form.")

