<!-- loioa61107a184f21015859ec14b47a3607f -->

# Common Elements in SQL Syntax in Data Lake Relational Engine

Language elements that are found in the syntax of many SQL statements.

-   column-name – an identifier that represents the name of a column.
-   condition – an expression that evaluates to TRUE, FALSE, or UNKNOWN.
-   connection-name – a string representing the name of an active connection.
-   data-type – a storage data type.
-   expression – an expression.
-   filename – a string containing a file name.
-   host-variable – a C language variable, declared as a host variable, preceded by a colon.
-   indicator-variable – a second host variable of type `short int` immediately following a normal host variable. An indicator variable must also be preceded by a colon. Indicator variables are used to pass NULL values to and from the database.
-   number – any sequence of digits followed by an optional decimal part and preceded by an optional negative sign. Optionally, the number can be followed by an ‘e’ and then an exponent. For example,

    ```
    42
    -4.038
    .001
    3.4e10
    1e-10
    ```

-   owner – an identifier representing the user ID who owns a database object.
-   role-name – an identifier representing the role name of a foreign key.
-   savepoint-name – an identifier that represents the name of a savepoint.
-   search-condition – a condition that evaluates to TRUE, FALSE, or UNKNOWN.
-   special-value – one of the special values described in *Special Values*.
-   statement-label – an identifier that represents the label of a loop or compound statement.
-   table-list – a list of table names, which might include correlation names. For more information, see *FROM clause*.
-   table-name – an identifier that represents the name of a table.
-   userid – an identifier representing a user name. The user ID is not case-sensitive and is unaffected by the setting of the `CASE RESPECT` property of the database.
-   variable-name – an identifier that represents a variable name.

**Related Information**  


[Special Values in Data Lake Relational Engine](../010-sql-language-elements/special-values-in-data-lake-relational-engine-a506dde.md "Special values can be used in expressions, and as column defaults when creating tables.")

[FROM Clause for Data Lake Relational Engine](from-clause-for-data-lake-relational-engine-a7749cf.md "Specifies the database tables or views involved in a SELECT statement.")

[Search Conditions in Data Lake Relational Engine](../010-sql-language-elements/search-conditions-in-data-lake-relational-engine-a4fa3d9.md "Conditions are used to choose a subset of the rows from a table, or in a control statement such as an IF statement to determine control of flow.")

[Expressions in Data Lake Relational Engine](../010-sql-language-elements/expressions-in-data-lake-relational-engine-a4ee102.md "Expressions are formed from different kinds of elements, such as constants, column names, SQL operators, and subqueries.")

[Strings in Data Lake Relational Engine](../010-sql-language-elements/strings-in-data-lake-relational-engine-a4ed4ed.md "Strings are either literal strings, or expressions with CHAR or VARCHAR data types.")

[Identifiers in Data Lake Relational Engine](../010-sql-language-elements/identifiers-in-data-lake-relational-engine-a4eca8f.md "Identifiers are names of objects in the database, such as user IDs, tables, and columns.")

