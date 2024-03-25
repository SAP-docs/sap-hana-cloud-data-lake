<!-- loioa7749cf084f21015b73b899c1520fb06 -->

# FROM Clause for Data Lake Relational Engine

Specifies the database tables or views involved in a `SELECT` statement.



```
...FROM <table-expression> [,...]

<table-expression> ::=
   { <table-name>
   | <view-name>
   | <procedure-name>
   | <common-table-expression>
   | ( <subquery> ) [ [ AS ] <derived-table-name> ( <column_name, ...>) ]
   | <derived-table>
   | <join-expression> 
   | ( <table-expression> , ... )
   | <openstring-expression>
   | <apply-expression>
   | <contains-expression>
   | <dml-derived-table>
   | <openxml-operator> }
```

```
<table-name> ::=
   [ <owner>.]<table-name> ]
   [ [ AS ] <correlation-name> ]
   [ FORCE INDEX ( <index-name> ) ]
```

```
<view-name> ::=
   [ <owner>.]<view-name> [ [ AS ] <correlation-name> ]
```

```
<procedure-name> ::=
   [  <owner>.]<procedure-name> ( [ <parameter>, ...])
   [  WITH (<column-name datatype>, )]
   [ [ AS ] <correlation-name> ]
```

```
<parameter> ::=
   { <scalar-expression> | <table-parameter> }
```

```
<table-parameter> ::= 
   TABLE (<select-statement)> [ OVER ( <table-parameter-over> ) ]
```

```
<table-parameter-over> ::=
   [ PARTITION BY { ANY | NONE | < table-expression> } ] 
   [ ORDER BY { <expression> | <integer> } ]
   [ { ASC | DESC } [, ...] ]
```

```
<derived-table> ::=
   ( <select-statement> ) [ AS ] <correlation-name> [ ( <column-name>, ... ) ]
```

```
<join-expression> ::=
   <table-expression> <join-operator> <table-expression>
   [ ON <join-condition> ]
```

```
<join-operator> ::=
   [ { KEY | NATURAL } ] { [ <join-type> ] JOIN | CROSS JOIN }
```

```
<join-type> ::=
   { INNER
   | LEFT [ OUTER ]
   | RIGHT [ OUTER ]
   | FULL [ OUTER ] }
```

```
<openstring-expression> ::=
   OPENSTRING ( { FILE | VALUE } <string-expression> )
   WITH ( <rowset-schema> ) 
   [ OPTION ( <scan-option> ...  ) ]
   [ AS ] <correlation-name>
```

```
<apply-expression> ::=
   <table-expression> { CROSS | OUTER } APPLY <table-expression>
```

```
<contains-expression> ::=
   { <table-name>  | <view-name> } CONTAINS 
   ( <column-name> [,...], <contains-query> ) 
   [ [ AS ] <score-correlation-name> ]
```

```
<rowset-schema> ::=
   { <column-schema-list>
   | TABLE [<owner>.]<table-name> [ ( <column-list> ) ] }
```

```
<column-schema-list> ::=
   { <column-name user-or-base-type> | filler( ) } [, ... ]
```

```
<column-list> ::=
   { <column-name> | filler( ) } [, ... ]
```

```
<scan-option> ::=
   { BYTE ORDER MARK { ON | OFF }
   | COMMENTS INTRODUCED BY <comment-prefix>
   | DELIMITED BY <string>
   | ENCODING <encoding>
   | ESCAPE CHARACTER <character>
   | ESCAPES { ON | OFF }
   | FORMAT { TEXT  | BCP  }
   | HEXADECIMAL { ON | OFF }
   | QUOTE <string>
   | QUOTES { ON | OFF }
   | ROW DELIMITED BY string
   | SKIP <integer>
   | STRIP { ON | OFF | LTRIM | RTRIM | BOTH } }
```

```
<contains-query> ::= <string>
```

```
<dml-derived-table> ::=
   ( <dml-statement>  ) REFERENCING ( [ { <table-version-names>  | NONE } ] )
```

```
<dml-statement> ::=
   { <insert-statement> 
   | <update-statement>
   } <delete-statement> }
```

```
<table-version-names> ::=
   { OLD [ AS ] <correlation-name> [ FINAL [ AS ] <correlation-name> ]
   | FINAL [ AS ] <correlation-name> }
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa7749cf084f21015b73b899c1520fb06__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

*<table-name\>*

</b></dt>
<dd>

A base table or temporary table. Tables owned by a different user can be qualified by specifying the user ID. Tables owned by groups to which the current user belongs are found by default without specifying the user ID.



</dd><dt><b>

*<view-name\>*

</b></dt>
<dd>

Specifies a view to include in the query. As with tables, views owned by a different user can be qualified by specifying the user ID. Views owned by groups to which the current user belongs are found by default without specifying the user ID. Although the syntax permits table hints on views, these hints have no effect.



</dd><dt><b>

*<procedure-name\>*

</b></dt>
<dd>

A stored procedure that returns a result set. This clause applies to the FROM clause of SELECT statements only. The parentheses following the procedure name are required even if the procedure does not take parameters. DEFAULT can be specified in place of an optional parameter.



</dd><dt><b>

*<parameter\>*

</b></dt>
<dd>

Specifies one of the following clauses:

-   *<scalar-parameter\>* – any objects of a valid SQL datatype.
-   *<table-parameter\>* – can be specified using a table, view or common table-expression name, which are treated as new instance of this object if the object is also used outside the table-parameter.

If a subquery is used to define the TABLE parameter, then the following restrictions must hold:

-   The table-parameter clause must be of type IN.
-   PARTITION BY or ORDER BY clauses must refer to the columns of the derived table and outer references. An expression in the *<expression-list\>* can be an integer K, which refers to the Kth column of the TABLE input parameter.



</dd><dt><b>

PARTITION BY

</b></dt>
<dd>

Logically specifies how the invocation of the function will be performed by the execution engine. The execution engine must invoke the function for each partition and the function must process a whole partition in each invocation. PARTITION BY or ORDER BY clauses must refer to the columns of the derived table and outer references. An expression in the expression-list can be an integer K, which refers to the Kth column of the TABLE input parameter.

PARTITION BY clause also specifies how the input data must be partitioned such that each invocation of the function will process exactly one partition of data. The function must be invoked the number of times equal to the number of partitions.

You can specify only one TABLE input parameter for PARTITION BY *<expression-list\>* or PARTITION BY ANY clause. For all other TABLE input parameters you must specify, explicit or implicit PARTITION BY NONE clause.

> ### Note:  
> The execution engine can invoke the function in any order of the partitions and the function is assumed to return the same result sets regardless of the partitions order. Partitions cannot be split among two invocations of the function.



</dd><dt><b>

ORDER BY

</b></dt>
<dd>

Specifies that the input data in each partition is expected to be sorted by *<expression-list\>* by the execution engine. If only one partition exists, the whole input data is ordered based on the ORDER BY specification. ORDER BY clause can be specified for any of the TABLE input parameters with PARTITION BY NONE or without PARTITION BY clause.



</dd><dt><b>

*<derived-table\>*

</b></dt>
<dd>

PARTITION BY or ORDER BY clauses mustYou can supply a SELECT statement instead of table or view name in the FROM clause. A SELECT statement used in this way is called a derived table, and it must be given an alias.



</dd><dt><b>

*<join-expression\>*, *<join-operator\>*, *<join-type\>*

</b></dt>
<dd>

The `join-type` keywords are:

-   CROSS JOIN – returns the Cartesian product \(cross product\) of the two source tables
-   NATURAL JOIN – compares for equality all corresponding columns with the same names in two tables \(a special case equijoin; columns are of same length and data type\)
-   KEY JOIN – restricts foreign-key values in the first table to be equal to the primary-key values in the second table
-   INNER JOIN – discards all rows from the result table that do not have corresponding rows in both tables
-   LEFT OUTER JOIN – preserves unmatched rows from the left table, but discards unmatched rows from the right table
-   RIGHT OUTER JOIN – preserves unmatched rows from the right table, but discards unmatched rows from the left table
-   FULL OUTER JOIN – retains unmatched rows from both the left and the right tables

Do not mix comma-style joins and keyword-style joins in the `FROM` clause. The same query can be written two ways, each using one of the join styles. The ANSI syntax keyword style join is preferable.

The ON clause filters the data of inner, left, right, and full joins. Cross joins do not have an ON clause. In an inner join, the ON clause is equivalent to a WHERE clause. In outer joins, however, the ON and WHERE clauses are different. The ON clause in an outer join filters the rows of a cross product and then includes in the result the unmatched rows extended with nulls. The WHERE clause then eliminates rows from both the matched and unmatched rows produced by the outer join. You must take care to ensure that unmatched rows you want are not eliminated by the predicates in the WHERE clause.

You cannot use subqueries inside an outer join ON clause.



</dd><dt><b>

*<openstring-expression\>*

</b></dt>
<dd>

Specify an OPENSTRING clause to query within a file or a BLOB, treating the content of these sources as a set of rows. When doing so, you also specify information about the schema of the file or BLOB for the result set to be generated, since you are not querying a defined structure such as a table or view. This clause applies to the FROM clause of a SELECT statement. It is not supported for UPDATE or DELETE statements.



</dd><dt><b>

*<apply-expression\>*

</b></dt>
<dd>

Use this clause to specify a join condition where the right table-expression is evaluated for every row in the left table-expression. For example, you can use an apply expression to evaluate a function, procedure, or derived table for each row in a table expression.



</dd><dt><b>

*<contains-expression\>*

</b></dt>
<dd>

Use the CONTAINS clause after a table name to filter the table, and return only those rows matching the full text query specified with contains-query. Every matching row of the table is returned, along with a score column that can be referred to using score-correlation-name, if it is specified. If score-correlation-name is not specified, then the score column can be referred to by the default correlation name, contains.



</dd><dt><b>

*<dml-derived-table\>*

</b></dt>
<dd>

Supports the use of a DML statement \(INSERT, UPDATE, or DELETE\) as a table expression in a query's FROM clause.



</dd><dt><b>

*<openxml-operator\>*

</b></dt>
<dd>

Use this parameter to return a result set from an XML document, by using the OPENXML operator.



</dd>
</dl>



<a name="loioa7749cf084f21015b73b899c1520fb06__IQ_Usage"/>

## Remarks

The `SELECT` statement requires a table list to specify which tables are used by the statement.

> ### Note:  
> Although this description refers to tables, it also applies to views unless otherwise noted.

The `FROM` table list creates a result set consisting of all the columns from all the tables specified. Initially, all combinations of rows in the component tables are in the result set, and the number of combinations is usually reduced by join conditions and/or `WHERE` conditions.

Tables owned by a different user can be qualified by specifying the *<owner\>*. Tables owned by roles to which the current user belongs are found by default without specifying the user ID.

The correlation name is used to give a temporary name to the table for this SQL statement only. This is useful when referencing columns that must be qualified by a table name but the table name is long and cumbersome to type. The correlation name is also necessary to distinguish between table instances when referencing the same table more than once in the same query. If no correlation name is specified, then the table name is used as the correlation name for the current statement.

If the same correlation name is used twice for the same table in a table expression, that table is treated as if it were only listed once. For example, in:

```
SELECT *
FROM SalesOrders
KEY JOIN SalesOrderItems,
SalesOrders
KEY JOIN Employees;
```

The two instances of the `SalesOrders` table are treated as one instance that is equivalent to:

```
SELECT *
FROM SalesOrderItems
KEY JOIN SalesOrders
KEY JOIN Employees;
```

By contrast, the following is treated as two instances of the `Person` table, with different correlation names HUSBAND and WIFE:

```
SELECT *
FROM Person HUSBAND, Person WIFE;
```

Join columns require like data types for optimal performance.



### Performance Considerations

Depending on the query, data lake Relational Engine allows between 16 and 64 tables in the `FROM` clause with the optimizer turned on; however, performance might suffer if you have more than 16 to 18 tables in the `FROM` clause in very complex queries.

> ### Note:  
> If you omit the `FROM` clause, or if all tables in the query are in the `SYSTEM` dbspace, the query is processed by SAP SQL Anywhere instead of data lake Relational Engine and might behave differently, especially with respect to syntactic and semantic restrictions and the effects of option settings.
> 
> If you have a query that does not require a `FROM` clause, you can force the query to be processed by data lake Relational Engine by adding the clause `FROM iq_dummy`, where `iq_dummy` is a one-row, one-column table that you create in your database.

Must be connected to the database.



<a name="loioa7749cf084f21015b73b899c1520fb06__IQ_Permissions"/>

## Privileges

The privileges required depend on the clause used.


<table>
<tr>
<th valign="top">

Clause

</th>
<th valign="top">

Privilege Required

</th>
</tr>
<tr>
<td valign="top">

FILE clause of *<openstring-expression\>*

</td>
<td valign="top">

READ FILE system privilege

</td>
</tr>
<tr>
<td valign="top">

TABLE clause of *<openstring-expression\>*

</td>
<td valign="top">

Requires one of the following:

-   You own the referenced tables
-   SELECT ANY TABLE object privilege.



</td>
</tr>
<tr>
<td valign="top">

All other clauses

</td>
<td valign="top">

None

</td>
</tr>
</table>

See [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md) for assistance with granting privileges



<a name="loioa7749cf084f21015b73b899c1520fb06__IQ_Standards"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products – the `JOIN` clause is not supported in some versions of SAP Adaptive Server Enterprise. Instead, you must use the `WHERE` clause to build joins



<a name="loioa7749cf084f21015b73b899c1520fb06__IQ_Examples"/>

## Examples

-   The following example shows valid `FROM` clauses:

    ```
    ...
    FROM Employees
    ...
    ...
    FROM Employees NATURAL JOIN Departments
    ...
    ...
    FROM Customers
    KEY JOIN SalesOrders
    KEY JOIN SalesOrderItems
    KEY JOIN Products
    ...;
    ```

-   The following example shows a query that illustrates how to use derived tables in a query:

    ```
    SELECT Surname, GivenName, number_of_orders
    FROM Customers JOIN
         ( SELECT CustomerID, count(*)
           FROM SalesOrders
            GROUP BY CustomerID )
         AS sales_order_counts ( CustomerID, 
                                 number_of_orders )
    ON ( Customers.ID = sales_order_counts.cust_id )
    WHERE number_of_orders > 3;
    ```

-   The following example shows a query that illustrates a valid `FROM` clause where the two references to the same table T are treated as two different instances of the same table T:

    ```
    SELECT * FROM T, my_proc(TABLE(SELECT T.Z, T.X FROM T)
    OVER(PARTITION BY T.Z));
    ```

-   The following example contains a derived table, MyDerivedTable, which ranks products in the Products table by UnitPrice:

    ```
    SELECT TOP 3 *
      FROM ( SELECT Description, 
             Quantity, 
             UnitPrice,
             RANK() OVER ( ORDER BY UnitPrice ASC ) 
             AS Rank 
             FROM Products ) AS MyDerivedTable
             ORDER BY Rank;
    ```

-   The following example shows query uses a comma-style join:

    ```
    SELECT *
      FROM Products pr, SalesOrders so, SalesOrderItems si
      WHERE pr.ProductID = so.ProductID
        AND pr.ProductID = si.ProductID;
    ```

    The same query can use the preferable keyword-style join:

    ```
    SELECT *
      FROM Products pr INNER JOIN SalesOrders so
        ON (pr.ProductID = so.ProductID)
      INNER JOIN SalesOrderItems si
        ON (pr.ProductID = si.ProductID);
    ```


**Related Information**  


[DELETE Statement for Data Lake Relational Engine](delete-statement-for-data-lake-relational-engine-a61b555.md "Deletes all the rows from the named table that satisfy the search condition. If no WHERE clause is specified, all rows from the named table are deleted.")

[SELECT Statement for Data Lake Relational Engine](select-statement-for-data-lake-relational-engine-a624e72.md "Retrieves information from the database.")

[FROM Clause for Full Text Searches](https://help.sap.com/viewer/a8937bea84f21015a80bc776cf758d50/2024_1_QRC/en-US/a5f8ddf384f210159ed4b49306dfae5f.html "Specifies the database tables or views involved in a SELECT statement.") :arrow_upper_right:

[FROM Clause for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/ccd090fa57a84916b181a47c6ba634e1.html "Specifies the database tables or views involved in a SELECT statement.") :arrow_upper_right:

[REVOKE Object-Level Privilege Statement for Data Lake Relational Engine](revoke-object-level-privilege-statement-for-data-lake-relational-engine-a3e7af2.md "Removes object-level privileges that were given using the GRANT statement.")

