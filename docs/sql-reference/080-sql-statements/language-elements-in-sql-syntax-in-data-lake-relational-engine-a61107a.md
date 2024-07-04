<!-- loioa61107a184f21015859ec14b47a3607f -->

# Language Elements in SQL Syntax in Data Lake Relational Engine

A list of language elements that are found in the syntax of many SQL statements.




<dl>
<dt><b>

column-name

</b></dt>
<dd>

An identifier that represents the name of a column.



</dd><dt><b>

condition

</b></dt>
<dd>

An expression that evaluates to TRUE, FALSE, or UNKNOWN.



</dd><dt><b>

connection-name

</b></dt>
<dd>

A string representing the name of an active connection.



</dd><dt><b>

data-type

</b></dt>
<dd>

A storage data type.



</dd><dt><b>

expression

</b></dt>
<dd>

An expression.



</dd><dt><b>

filename

</b></dt>
<dd>

A string containing a file name.



</dd><dt><b>

host-variable

</b></dt>
<dd>

A C language variable, declared as a host variable, preceded by a colon.



</dd><dt><b>

indicator-variable

</b></dt>
<dd>

A second host variable of type `short int` immediately following a normal host variable. An indicator variable must also be preceded by a colon. Indicator variables are used to pass NULL values to and from the database.



</dd><dt><b>

number

</b></dt>
<dd>

Any sequence of digits followed by an optional decimal part and preceded by an optional negative sign. Optionally, the number can be followed by an ‘e’ and then an exponent. For example,

```
42
-4.038
.001
3.4e10
1e-10
```



</dd><dt><b>

owner

</b></dt>
<dd>

An identifier representing the user ID who owns a database object.



</dd><dt><b>

query-block

</b></dt>
<dd>

A query block is a simple query expression, or a query expression with an ORDER BY clause.



</dd><dt><b>

role-name

</b></dt>
<dd>

An identifier representing the role name of a foreign key.



</dd><dt><b>

savepoint-name

</b></dt>
<dd>

An identifier that represents the name of a savepoint.



</dd><dt><b>

search-condition

</b></dt>
<dd>

A condition that evaluates to TRUE, FALSE, or UNKNOWN.



</dd><dt><b>

special-value

</b></dt>
<dd>

one of the special values described in *Special Values*.



</dd><dt><b>

statement-label

</b></dt>
<dd>

An identifier that represents the label of a loop or compound statement.



</dd><dt><b>

table-list

</b></dt>
<dd>

A list of table names, which might include correlation names. For more information, see *FROM clause*.



</dd><dt><b>

table-name

</b></dt>
<dd>

An identifier that represents the name of a table.



</dd><dt><b>

userid

</b></dt>
<dd>

An identifier representing a user name. The user ID is not case-sensitive and is unaffected by the setting of the `CASE RESPECT` property of the database.



</dd><dt><b>

variable-name

</b></dt>
<dd>

An identifier that represents a variable name.



</dd>
</dl>

**Related Information**  


[Special Values in Data Lake Relational Engine](../010-sql-language-elements/special-values-in-data-lake-relational-engine-a506dde.md "Special values can be used in expressions, and as column defaults when creating tables.")

[FROM Clause for Data Lake Relational Engine](from-clause-for-data-lake-relational-engine-a7749cf.md "Specifies the objects involved in a SELECT, DELETE or UPDATE statement.")

[Search Conditions in Data Lake Relational Engine](../010-sql-language-elements/search-conditions-in-data-lake-relational-engine-a4fa3d9.md "Conditions are used to choose a subset of the rows from a table, or in a control statement such as an IF statement to determine control of flow.")

[Expressions in Data Lake Relational Engine](../010-sql-language-elements/expressions-in-data-lake-relational-engine-a4ee102.md "Expressions are formed from different kinds of elements, such as constants, column names, SQL operators, and subqueries.")

[Strings in Data Lake Relational Engine](../010-sql-language-elements/strings-in-data-lake-relational-engine-a4ed4ed.md "Strings are either literal strings, or expressions with CHAR or VARCHAR data types.")

[Identifiers in Data Lake Relational Engine](../010-sql-language-elements/identifiers-in-data-lake-relational-engine-a4eca8f.md "Identifiers are names of objects in the database, such as user IDs, tables, and columns.")

