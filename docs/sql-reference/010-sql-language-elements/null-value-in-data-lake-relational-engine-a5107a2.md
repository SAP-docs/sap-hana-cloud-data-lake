<!-- loioa5107a2e84f2101595bd9bacac97b5be -->

# NULL Value in Data Lake Relational Engine

Use NULL to specify a value that is unknown, missing, or not applicable.



## Remarks

The NULL value is a special value that is different from any valid value for any data type. However, the NULL value is a legal value in any data type. These are two separate and distinct cases where NULL is used:


<table>
<tr>
<th valign="top" rowspan="1">

Situation



</th>
<th valign="top" rowspan="1">

Description



</th>
</tr>
<tr>
<td valign="top" rowspan="1">

missing



</td>
<td valign="top" rowspan="1">

The field does have a value, but that value is unknown.



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

inapplicable



</td>
<td valign="top" rowspan="1">

The field does not apply for this particular row.



</td>
</tr>
</table>

SQL allows columns to be created with the NOT NULL restriction. This means that those particular columns cannot contain the NULL value.

The NULL value introduces the concept of three valued logic to SQL. The NULL value compared using any comparison operator with any value including the NULL value is UNKNOWN. The only search condition that returns TRUE is the IS NULL predicate. In SQL, rows are selected only if the search condition in the WHERE clause evaluates to TRUE; rows that evaluate to UNKNOWN or FALSE are not selected.

You can also use the IS \[ NOT \] *<truth-value\>* clause, where *<truth-value\>* is one of TRUE, FALSE or UNKNOWN, to select rows where the NULL value is involved.

In the following examples, the column Salary contains the NULL value.


<table>
<tr>
<th valign="top" rowspan="1">

Condition



</th>
<th valign="top" rowspan="1">

Truth Value



</th>
<th valign="top" rowspan="1">

Selected?



</th>
</tr>
<tr>
<td valign="top" rowspan="1">

Salary = NULL



</td>
<td valign="top" rowspan="1">

UNKNOWN



</td>
<td valign="top" rowspan="1">

NO



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

Salary <\> NULL



</td>
<td valign="top" rowspan="1">

UNKNOWN



</td>
<td valign="top" rowspan="1">

NO



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

NOT \(Salary = NULL\)



</td>
<td valign="top" rowspan="1">

UNKNOWN



</td>
<td valign="top" rowspan="1">

NO



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

NOT \(Salary <\> NULL\)



</td>
<td valign="top" rowspan="1">

UNKNOWN



</td>
<td valign="top" rowspan="1">

NO



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

Salary = 1000



</td>
<td valign="top" rowspan="1">

UNKNOWN



</td>
<td valign="top" rowspan="1">

NO



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

Salary IS NULL



</td>
<td valign="top" rowspan="1">

TRUE



</td>
<td valign="top" rowspan="1">

YES



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

Salary IS NOT NULL



</td>
<td valign="top" rowspan="1">

FALSE



</td>
<td valign="top" rowspan="1">

NO



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

Salary = 1000 IS UNKNOWN



</td>
<td valign="top" rowspan="1">

TRUE



</td>
<td valign="top" rowspan="1">

YES



</td>
</tr>
</table>

The same rules apply when comparing columns from two different tables. Therefore, joining two tables together does not select rows where any of the columns compared contain the NULL value.

The NULL value also has an interesting property when used in numeric expressions. The result of any numeric expression involving the NULL value is the NULL value. This means that if the NULL value is added to a number, the result is the NULL value—not a number. If you want the NULL value to be treated as 0, then must use the ISNULL\( expression, 0 \) function.

Many common errors in formulating SQL queries are caused by the behavior of NULL. Be careful to avoid these problem areas. Note the effect of three-valued logic when combining search conditions.



```
NULL
```



<a name="loioa5107a2e84f2101595bd9bacac97b5be__iq_refbb_148"/>

## Permissions

Must be connected to the database



<a name="loioa5107a2e84f2101595bd9bacac97b5be__iq_refbb_149"/>

## Side Effects

None



<a name="loioa5107a2e84f2101595bd9bacac97b5be__iq_refbb_150"/>

## Example

The following INSERT statement inserts a NULL into the date\_returned column of the Borrowed\_book table:

```
INSERT
INTO Borrowed_book
( date_borrowed, date_returned, book )
VALUES ( CURRENT DATE, NULL, '1234' ); 
```

**Related Information**  


[NULL Value in Data Lake Relational Engine](null-value-in-data-lake-relational-engine-a5107a2.md "Use NULL to specify a value that is unknown, missing, or not applicable.")

[SQL Operators in Data Lake Relational Engine](sql-operators-in-data-lake-relational-engine-a4f0a69.md "These topics describe the arithmetic, string, and bitwise operators available in data lake Relational Engine.")

[Subqueries in Search Conditions](subqueries-in-search-conditions-a4fb435.md "A subquery is a SELECT statement enclosed in parentheses. Such a SELECT statement must contain one and only one select list item.")

[Comparison Conditions](comparison-conditions-a4fabf2.md "Comparison conditions in search conditions use a comparison operator.")

[Expressions in Data Lake Relational Engine](expressions-in-data-lake-relational-engine-a4ee102.md "Expressions are formed from different kinds of elements, such as constants, column names, SQL operators, and subqueries.")

[Search Conditions in Data Lake Relational Engine](search-conditions-in-data-lake-relational-engine-a4fa3d9.md "Conditions are used to choose a subset of the rows from a table, or in a control statement such as an IF statement to determine control of flow.")

[Strings in Data Lake Relational Engine](strings-in-data-lake-relational-engine-a4ed4ed.md "Strings are either literal strings, or expressions with CHAR or VARCHAR data types.")

[Three-Valued Logic](three-valued-logic-a501bc6.md "The AND, OR, NOT, and IS logical operators of SQL work in three-valued logic.")

