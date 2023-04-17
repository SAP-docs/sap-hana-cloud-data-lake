<!-- loio3e6f6d3a15f74a52b4ecaf84e14d60c6 -->

# Common Elements in SQL Syntax in Data Lake Relational Engine \(SAP HANA DB-Managed\)

Language elements that are found in the syntax of many data lake Relational Engine SQL statements.

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

-   *<relational\_container\_schema\_name\>* – an identifier representing the user ID who owns a database object. In data lake Relational Engine, there’s only one schema. All connections to data lake Relational Engine connect using the same user ID. Therefore, all objects created have the same schema \(owner\).
-   role-name – an identifier representing the role name of a foreign key.
-   savepoint-name – an identifier that represents the name of a savepoint.
-   search-condition – a condition that evaluates to TRUE, FALSE, or UNKNOWN.
-   special-value – one of the special values described in *Special Values in Data Lake Relational Engine*.
-   statement-label – an identifier that represents the label of a loop or compound statement.
-   table-list – a list of table names, which can include correlation names. For more information, see *FROM Clause in Data Lake Relational Engine*.
-   *<data\_lake\_table\_name\>* – an identifier that represents the name of a table.
-   variable-name – an identifier that represents a variable name.

**Related Information**  


[FROM Clause for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/from-clause-for-data-lake-relational-engine-sap-hana-db-managed-ccd090f.md "Specifies the database tables or views involved in a SELECT statement.")

[Special Values in Data Lake Relational Engine \(SAP HANA DB-Managed\)](special-values-in-data-lake-relational-engine-sap-hana-db-managed-798c449.md "Special values can be used in expressions, and as column defaults when creating tables.")

