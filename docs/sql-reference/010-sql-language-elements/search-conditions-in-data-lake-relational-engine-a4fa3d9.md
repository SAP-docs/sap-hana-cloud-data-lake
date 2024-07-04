<!-- loioa4fa3d9e84f21015a4a6a9424156ed9e -->

# Search Conditions in Data Lake Relational Engine

Conditions are used to choose a subset of the rows from a table, or in a control statement such as an IF statement to determine control of flow.



## Remarks

SQL conditions do not follow Boolean logic, where conditions are either true or false. In SQL, every condition evaluates as one of TRUE, FALSE, or UNKNOWN. This is called three-valued logic. The result of a comparison is UNKNOWN if either value being compared is the NULL value.

Rows satisfy a search condition if and only if the result of the condition is TRUE. Rows for which the condition is UNKNOWN do not satisfy the search condition.

Subqueries form an important class of expression that is used in many search conditions.

The different types of search conditions are discussed in the following sections.

You specify a search condition for a WHERE clause, a HAVING clause, a CHECK clause, a JOIN clause, or an IF expression.



```
{ <expression> <compare> <expression>
| <expression> <compare> { ANY | SOME| ALL } ( <subquery> )
| <expression> IS [ NOT ] NULL <expression>
| <expression1> IS [ NOT ] DISTINCT FROM <expression2>
| <expression> [ NOT ] BETWEEN <expression> AND <expression>
| <expression> [ NOT ] LIKE <expression> [ ESCAPE <expression> ]
| <expression> [ NOT ] IN ( { <expression>| <subquery> |
… <value-expr1>, <value-expr2> [, <value-expr3> ] … } )
| <column-name> [ NOT ] CONTAINS ( … <word1 >[, <word2> ] [, <word3> ] … )
| CONTAINS ( <column-name> [, <… >], <contains-query string>)
| EXISTS ( <subquery> )
| NOT <condition>
| <condition> AND <condition>
| <condition> OR <condition>
| ( <condition> )
| ( <condition>, <estimate> )
| <condition> IS [ NOT ] { TRUE | FALSE | UNKNOWN }
```

```
<compare> ::=
{ = | > | < | >= | <= | <> | != | !< | !> }
```



<a name="loioa4fa3d9e84f21015a4a6a9424156ed9e__iq_refbb_76"/>

## Authorization

Must be connected to the database.



<a name="loioa4fa3d9e84f21015a4a6a9424156ed9e__iq_refbb_78"/>

## Side Effects

None



<a name="loioa4fa3d9e84f21015a4a6a9424156ed9e__iq_refbb_77"/>

## Examples

The following query retrieves the names and birth years of the oldest employees:

```
SELECT Surname, BirthDate 
FROM Employees 
WHERE BirthDate <= ALL (SELECT BirthDate FROM Employees);
```

The subqueries that provide comparison values for quantified comparison predicates might retrieve multiple rows but can have only one column.

**Related Information**  


[SQL Operators in Data Lake Relational Engine](sql-operators-in-data-lake-relational-engine-a4f0a69.md "These topics describe the arithmetic, string, and bitwise operators available in data lake Relational Engine.")

[Subqueries in Search Conditions](subqueries-in-search-conditions-a4fb435.md "A subquery is a SELECT statement enclosed in parentheses. Such a SELECT statement must contain one and only one select list item.")

[Comparison Conditions](comparison-conditions-a4fabf2.md "Comparison conditions in search conditions use a comparison operator.")

[Expressions in Data Lake Relational Engine](expressions-in-data-lake-relational-engine-a4ee102.md "Expressions are formed from different kinds of elements, such as constants, column names, SQL operators, and subqueries.")

[NULL Value in Data Lake Relational Engine](null-value-in-data-lake-relational-engine-a5107a2.md "Use NULL to specify a value that is unknown, missing, or not applicable.")

[Strings in Data Lake Relational Engine](strings-in-data-lake-relational-engine-a4ed4ed.md "Strings are either literal strings, or expressions with CHAR or VARCHAR data types.")

[Three-Valued Logic](three-valued-logic-a501bc6.md "The AND, OR, NOT, and IS logical operators of SQL work in three-valued logic.")

