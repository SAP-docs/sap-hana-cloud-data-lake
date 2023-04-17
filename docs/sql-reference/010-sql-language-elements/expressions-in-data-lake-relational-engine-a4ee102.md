<!-- loioa4ee102484f21015b16cbd0390ddf6ec -->

# Expressions in Data Lake Relational Engine

Expressions are formed from different kinds of elements, such as constants, column names, SQL operators, and subqueries.



```
expression:
<case-expression>
| <constant>
| [ <correlation-name>. ] <column-name >
| - <expression>
| <expression operator> <expression>
| ( <expression> )
| <function-name> ( <expression>, … )
| <if-expression>
| ( <subquery> )
| <variable-name>
```

```
<case-expression> ::=
{ CASE <search-condition>
... WHEN <expression> THEN <expression> [ , … ]
... [ ELSE <expression> ] 
END
| CASE
... WHEN <search-condition> THEN <expression> [ , … ]
... [ ELSE <expression> ] 
END }
```

```
<constant> ::=
{ <integer> | <number> | '<string>'
 | <special-constant> | <host-variable> }
```

```
<special-constant> ::=
{ CURRENT { DATE | TIME | TIMESTAMP | USER }
| LAST USER
| NULL
| SQLCODE
| SQLSTATE }
```

```
<if-expression> ::=
IF <condition>
... THEN <expression>
... [ ELSE <expression> ]
ENDIF
```

```
<operator> ::=
{ + | - | * | / | || | % }
```

**Related Information**  


[SQL Operators in Data Lake Relational Engine](sql-operators-in-data-lake-relational-engine-a4f0a69.md "These topics describe the arithmetic, string, and bitwise operators available in data lake Relational Engine.")

[Subqueries in Search Conditions](subqueries-in-search-conditions-a4fb435.md "A subquery is a SELECT statement enclosed in parentheses. Such a SELECT statement must contain one and only one select list item.")

[Special Values in Data Lake Relational Engine](special-values-in-data-lake-relational-engine-a506dde.md "Special values can be used in expressions, and as column defaults when creating tables.")

[Comparison Conditions](comparison-conditions-a4fabf2.md "Comparison conditions in search conditions use a comparison operator.")

[NULL Value in Data Lake Relational Engine](null-value-in-data-lake-relational-engine-a5107a2.md "Use NULL to specify a value that is unknown, missing, or not applicable.")

[Search Conditions in Data Lake Relational Engine](search-conditions-in-data-lake-relational-engine-a4fa3d9.md "Conditions are used to choose a subset of the rows from a table, or in a control statement such as an IF statement to determine control of flow.")

[Strings in Data Lake Relational Engine](strings-in-data-lake-relational-engine-a4ed4ed.md "Strings are either literal strings, or expressions with CHAR or VARCHAR data types.")

[Three-Valued Logic](three-valued-logic-a501bc6.md "The AND, OR, NOT, and IS logical operators of SQL work in three-valued logic.")

