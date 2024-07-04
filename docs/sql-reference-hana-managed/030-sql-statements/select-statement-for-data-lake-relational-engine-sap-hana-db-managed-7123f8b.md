<!-- loio7123f8b4e1f14a8f9efd257794202198 -->

# SELECT Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Retrieves information from the database.



<a name="loio7123f8b4e1f14a8f9efd257794202198__section_rl5_1cd_x4b"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when connected as follows:

-   Connected to SAP HANA database as a SAP HANA database user.

When using the REMOTE\_EXECUTE procedure, the SELECT statement can only be included as part of the definition within the CREATE VIEW Statement. It can't be run on its own in a REMOTE\_EXECUTE procedure.

See [REMOTE EXECUTE/REMOTE\_EXECUTE\_DDL Usage Examples for Executing SQL Statements](https://help.sap.com/docs/SAP_HANA_DATA_LAKE/a898e08b84f21015969fa437e89860c8/fd99ac0ce9914c7695488ca4b2fa70f5.html).

For information on using REMOTE\_EXECUTE\_QUERY, see [Query Using REMOTE\_EXECUTE\_QUERY in Data Lake Relational Engine \(SAP HANA DB-Managed\)](https://help.sap.com/docs/SAP_HANA_DATA_LAKE/9220e7fec0fe4503b5c5a6e21d584e63/4192f252c2af4136aebadbd1a806b139.html).



```
SELECT 
   [ WITH <temporary-views> ]
   [ { ALL | DISTINCT } ] [ <row-limitation-option1> ] <select-list>
   [ <row-limitation-option2> ]
   [ INTO <variable-list>]
   [ INTO LOCAL TEMPORARY TABLE <table-name> ]
   [ FROM <schema-name> [,...] ]
   [ WHERE <search-condition> ]
   [ { GROUP BY <expression> [, ...]
      | ROLLUP ( <expression> [, ...] )
      | CUBE ( <expression> [, ...] ) } ]
   [ HAVING <search-condition> ]
   [ ORDER BY { <expression> | <integer> } [ { ASC | DESC } ] [,...] ]
   [ FOR XML <xml-mode> ]
   [ nopagenumber ]
   [ OPTION ( query-hint, ... ) ]
```

```
<temporary-views> :
   { <regular-view>, ...
    | RECURSIVE { <regular-view> | <recursive-view> }, ...
```

```
<regular-view> ::=
   <view-name> [ ( column-name, ... ) ] AS ( query-block )
```

```
<recursive-view> ::=
   <view-name> [ ( column-name, ... ) ] AS ( <initial-query-block> UNION ALL <recursive-query-block> )
```

For information on *<query-block\>*, see [Language Elements in SQL Syntax in Data Lake Relational Engine \(SAP HANA DB-Managed\)](language-elements-in-sql-syntax-in-data-lake-relational-engine-sap-hana-db-managed-3e6f6d3.md)

```
<row-limitation-option1> ::=
   { FIRST 
   | TOP { ALL | <limit-expression> } [ START AT <startat-expression> ] }
```

```
<limit-expression> | <offset-expression> | <offset-expression> ::=
   { <integer>
    | <variable>
    | ( <simple-expression> )
    | ( <simple-expression> { + | - | * } <simple-expression> ) }
```

```
<simple-expression> ::=
   { <integer>
    | <variable>
    | ( <simple-expression> )
    | ( <simple-expression> { + | - | * } <simple-expression> ) }
```

```
<select-list> ::=
   { <column-name>
    | <expression> [ [ AS ] <alias-name> ]
    | * }
```

```
<row-limitation-option2> ::=
   LIMIT { [ <offset-expression>, ] <limit-expression> 
   | <limit-expression> OFFSET <offset-expression> }
```

```
<variable-list> ::=
   { <host-variable-list> 
   | <variable-list> 
   | [ <schema-name>.]<table-name > } 
```

```
<query-hint> ::=
   { MATERIALIZED VIEW OPTIMIZATION <option-value>
    | FORCE OPTIMIZATION
    | FORCE NO OPTIMIZATION
    | <option-name>=<option-value>
    | <materialized_view_staleness_options_list> }
```

```
<option-value> : 
   {<hostvar> (indicator allowed)
    | <string>
    | <identifier>
    | <number> }
```

```
<materialized_view_staleness_options_list> ::=
   <materialized_view_staleness_option> [, ...]
```

```
<window-expression> ::= See WINDOW Clause for Data Lake Relational Engine (SAP HANA DB-Managed)
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio7123f8b4e1f14a8f9efd257794202198__section_w35_v4w_brb"/>

## Parameters


<dl>
<dt><b>

WITH or WITH RECURSIVE clause

</b></dt>
<dd>

Define one or more common table expressions, also known as temporary views, to be used elsewhere in the remainder of the statement. These expressions may be non-recursive, or may be self-recursive. Recursive common table expressions may appear alone, or intermixed with non-recursive table expressions, only if the RECURSIVE keyword is specified. Mutually recursive common table expressions are not supported.

This clause is permitted only if the SELECT query block appears in one of the following locations:

-   Within a top-level SELECT query block including the top-level SELECT query block of a view definition

-   Within a top-level SELECT statement within an INSERT query block

-   Within a nested SELECT query block defining a derived table in any type of SQL statement


Recursive expressions consist of an initial subquery and a recursive subquery. The initial-query implicitly defines the schema of the view. The recursive subquery must contain a reference to the view within the FROM clause. During each iteration, this reference refers only to the rows added to the view in the previous iteration. The reference must not appear on the null-supplying side of an outer join. A recursive common table expression must not use aggregate functions and must not contain a GROUP BY, ORDER BY, or DISTINCT clause.

The WITH clause is not supported with remote tables. The WITH clause may also be used in INTERSECT, UNION, and EXCEPT query blocks.

This functionality is available only in the Watcom SQL dialect.

```
WITH RECURSIVE
  manager ( EmployeeID, ManagerID,
            GivenName, Surname, mgmt_level ) AS
( ( SELECT EmployeeID, ManagerID,       -- initial subquery
           GivenName, Surname, 0
    FROM Employees AS e
    WHERE ManagerID = EmployeeID )
  UNION ALL
  ( SELECT e.EmployeeID, e.ManagerID,   -- recursive subquery
           e.GivenName, e.Surname, m.mgmt_level + 1
    FROM Employees AS e JOIN manager AS m
     ON   e.ManagerID =  m.EmployeeID
      AND e.ManagerID <> e.EmployeeID
      AND m.mgmt_level < 20 ) )
SELECT 'Manager', * FROM manager
WHERE mgmt_level > 0
UNION ALL
SELECT 'Employee', * FROM manager
WHERE mgmt_level = 0
ORDER BY mgmt_level, Surname, GivenName;

```



</dd><dt><b>

ALL or DISTINCT

</b></dt>
<dd>

Filters query results. If neither is specified, all rows that satisfy the clauses of the SELECT statement are retrieved. If DISTINCT is specified, duplicate output rows are eliminated. This is called the projection of the result of the statement. In many cases, statements take significantly longer to execute when DISTINCT is specified, so reserve the use of DISTINCT for cases where it is necessary.

If DISTINCT is used, the statement cannot contain an aggregate function with a DISTINCT parameter.



</dd><dt><b>

*<row-limitation-option1\>*

</b></dt>
<dd>

Specifies the number of rows returned from a query. FIRST returns the first row selected from the query. TOP returns the specified number of rows from the query where *<number-of-rows\>* is in the range 1 – 2147483647 and can be an integer constant or integer variable.

> ### Note:  
> You cannot use TOP and LIMIT in the same query.

FIRST and TOP are used primarily with the ORDER BY clause. If you use these keywords without an ORDER BY clause, the result might vary from run to run of the same query, as the optimizer might choose a different query plan.

FIRST and TOP are permitted only in the top-level SELECT of a query, so they cannot be used in derived tables or view definitions. Using FIRST or TOP in a view definition might result in the keyword being ignored when a query is run on the view.

Using FIRST is the same as setting the ROW\_COUNT database option to 1. Using TOP is the same as setting the ROW\_COUNT option to the same number of rows. If both TOP and ROW\_COUNT are set, then the value of TOP takes precedence.

The ROW\_COUNT option could produce inconsistent results when used in a query involving global variables, system functions or proxy tables. See *ROW\_COUNT Option* for details.



</dd><dt><b>

*<select-list\>*

</b></dt>
<dd>

Is a comma delimited list of expressions that specify what is retrieved from the database. If an asterisk \(\*\) is specified, all columns of all tables in the FROM clause \(table-name all columns of the named table\) are selected. Aggregate functions and analytical functions are allowed in the *<select-list\>*.

> ### Note:  
> In data lake Relational Engine, scalar subqueries \(nested selects\) are allowed in the select list of the top level SELECT, as in SAP SQL Anywhere and SAP Adaptive Server Enterprise. Subqueries cannot be used inside a conditional value expression \(for example, in a CASE statement\).
> 
> Subqueries can also be used in a WHERE or HAVING clause predicate \(one of the supported predicate types\). However, inside the WHERE or HAVING clause, subqueries cannot be used inside a value expression or inside a CONTAINS or LIKE predicate. Subqueries are not allowed in the ON clause of outer joins or in the GROUP BY clause.



</dd><dt><b>

*<alias-name\>*

</b></dt>
<dd>

Can be used throughout the query to represent the aliased expression. Alias names are also displayed by Interactive SQL at the top of each column of output from the SELECT statement. If the optional *<alias-name\>* is not specified after an expression, Interactive SQL displays the expression. If you use the same name or expression for a column alias as the column name, the name is processed as an aliased column, not a table column name.



</dd><dt><b>

INTO \{ *<host-variable-list\>* | *<variable-list\>* | *<table-name\>* \}

</b></dt>
<dd>

Specifies the following:

-   *<host-variable-list\>* – specifies where the results of the SELECT statement go. There must be one *<host-variable\>* item for each item in the *<select-list\>*. Select list items are put into the host variables in order. An indicator host variable is also allowed with each *<host-variable\>* so the program can tell if the select list item was NULL. Used in Embedded SQL only.

-   *<variable-list\>* – specifies where the results of the SELECT statement go. There must be one variable for each item in the select list. Select list items are put into the variables in order. Used in procedures only

-   *<table-name\>* – creates a table and fills the table with data. If the table name starts with \#, the table is created as a temporary table. Otherwise, the table is created as a permanent base table. For permanent tables to be created, the query must satisfy these conditions:

    -   The *<select-list\>* contains more than one item, and the INTO target is a single *<table-name\>* identifier, or
    -   The select-list contains a \* and the INTO target is specified as *<owner.table\>*.

    To create a permanent table with one column, the table name must be specified as *<owner.table\>*. Omit the owner specification for a temporary table.

    This statement causes a COMMIT before execution as a side effect of creating the table. Requires the CREATE TABLE system privilege to execute this statement. No permissions are granted on the new table: the statement is a short form for CREATE TABLE followed by INSERT... SELECT.

    A SELECT INTO from a stored procedure or function is not permitted, as SELECT INTO is an atomic statement and you cannot do COMMIT, ROLLBACK, or some ROLLBACK TO SAVEPOINT statements in an atomic statement.

    Tables created using this statement do not have a primary key defined. You can add a primary key using ALTER TABLE. A primary key should be added before applying any updates or deletes to the table; otherwise, these operations result in all column values being logged in the transaction log for the affected rows.

    Use of this clause is restricted to valid SAP SQL Anywhere queries. Data lake Relational Engine extensions are not supported.




</dd><dt><b>

INTO LOCAL TEMPORARY TABLE

</b></dt>
<dd>

Creates a local, temporary table and populates it with the results of the query. When you use this clause, you do not need to start the temporary table name with \#.



</dd><dt><b>

FROM

</b></dt>
<dd>

Retrieves rows and views specified in the *<object-list\>*.

```
<object-list> ::=
   [ { <owner> | <schema-name> }.] <object-name> [,...]
```

See also [FROM Clause for Data Lake Relational Engine \(SAP HANA DB-Managed\)](from-clause-for-data-lake-relational-engine-sap-hana-db-managed-ccd090f.md)

Joins can be specified using join operators. For more information, see *FROM Clause*. A SELECT statement with no FROM clause can be used to display the values of expressions not derived from tables. For example, the following displays the value of the @@version global variable:

```
SELECT @@version;
```

This is equivalent to:

```
SELECT @@version
FROM DUMMY;
```

> ### Note:  
> If you omit the FROM clause, or if all tables in the query are in the SYSTEM dbspace, the query is processed by SAP SQL Anywhere instead of data lake Relational Engine and might behave differently, especially with respect to syntactic and semantic restrictions and the effects of option settings.
> 
> If you have a query that does not require a FROM clause, you can force the query to be processed by data lake Relational Engine by adding the clause “FROM iq\_dummy,” where iq\_dummy is a one-row, one-column table that you create in your database.



</dd><dt><b>

WHERE *<search-condition\>*

</b></dt>
<dd>

Specifies which rows are selected from the tables named in the FROM clause.

The use of the same CASE statement is not allowed in both the SELECT and the WHERE clause of a grouped query.

Data lake Relational Engine also supports the disjunction of subquery predicates. Each subquery can appear within the WHERE or HAVING clause with other predicates and can be combined using the AND or OR operators.



</dd><dt><b>

GROUP BY

</b></dt>
<dd>

Groups columns, alias names, or functions. GROUP BY expressions must also appear in the select list. The result of the query contains one row for each distinct set of values in the named columns, aliases, or functions. The resulting rows are often referred to as groups since there is one row in the result for each group of rows from the table list. In the case of GROUP BY, all NULL values are treated as identical. Aggregate functions can then be applied to these groups to get meaningful results.

GROUP BY must contain more than a single constant. You do not need to add constants to the GROUP BY clause to select the constants in grouped queries. If the GROUP BY expression contains only a single constant, an error is returned and the query is rejected.

When GROUP BY is used, the select list, HAVING clause, and ORDER BY clause cannot reference any identifiers except those named in the GROUP BY clause. This exception applies: The *<select-list\>* and HAVING clause may contain aggregate functions.



</dd><dt><b>

ROLLUP operator

</b></dt>
<dd>

Subtotals GROUP BY expressions that roll up from a detailed level to a grand total.



</dd><dt><b>

CUBE operator

</b></dt>
<dd>

Analyzes data by forming the data into groups in more than one dimension. CUBE requires an ordered list of grouping expressions \(dimensions\) as arguments and enables the SELECT statement to calculate subtotals for all possible combinations of the group of dimensions. The CUBE operator is part of the GROUP BY clause.



</dd><dt><b>

HAVING *<search-condition\>*

</b></dt>
<dd>

Based on the group values and not on the individual row values. The HAVING clause can be used only if either the statement has a GROUP BY clause or if the select list consists solely of aggregate functions. Any column names referenced in the HAVING clause must either be in the GROUP BY clause or be used as a parameter to an aggregate function in the HAVING clause.



</dd><dt><b>

ORDER BY

</b></dt>
<dd>

Orders the results of a query. Each item in the ORDER BY list can be labeled as ASC for ascending order or DESC for descending order. Ascending is assumed if neither is specified. If the expression is an integer n, then the query results are sorted by the nth item in the select list.

In Embedded SQL, the SELECT statement is used for retrieving results from the database and placing the values into host variables with the INTO clause. The SELECT statement must return only one row. For multiple row queries, you must use cursors.

You cannot include a Java class in the SELECT list, but you can, for example, create a function or variable that acts as a wrapper for the Java class and then select it.



</dd><dt><b>

FOR XML

</b></dt>
<dd>

Specifies that the result set is to be returned as an XML document. The format of the XML depends on the mode you specify. Cursors declared with FOR XML are implicitly READ ONLY.

```
<xml-mode> ::=
   { RAW [ , ELEMENTS ] 
   | AUTO [ , ELEMENTS ] 
   | EXPLICIT }
```


<dl>
<dt><b>

RAW

</b></dt>
<dd>

Each row in the result set is represented as an XML <row\> element, and each column is represented as an attribute of the <row\> element.



</dd><dt><b>

AUTO

</b></dt>
<dd>

Returns the query results as nested XML elements. Each table referenced in the select-list is represented as an element in the XML. The order of nesting for the elements is based on the order that tables are referenced in the select-list.



</dd><dt><b>

EXPLICIT

</b></dt>
<dd>

Allows control of the form of the generated XML document. Using EXPLICIT mode offers more flexibility in naming elements and specifying the nesting structure than either RAW or AUTO mode.



</dd>
</dl>



</dd><dt><b>

*<row-limitation-option2\>*

</b></dt>
<dd>

Returns a subset of rows that satisfy the WHERE clause. Only one row-limitation clause can be specified at a time. When specifying this clause, an ORDER BY clause is required to order the rows in a meaningful manner. The row limitation clause is valid only in the top query block of a statement.

The LIMIT argument must be an integer or integer variable The OFFSET argument must evaluate to a value greater than or equal to 0. If *<offset-expression\>* is not specified, the default is 0.

The row limitation clause LIMIT *<offset-expression\>*, *<limit-expression\>* is equivalent to LIMIT *<limit-expression\>* OFFSET *<offset-expression\>*.

The LIMIT keyword is disabled by default. Use the RESERVED\_KEYWORDS option to enable the LIMIT keyword.

> ### Note:  
> You cannot specify TOP and LIMIT in the same query.



</dd><dt><b>

*<materialized\_view\_staleness\_options\>*

</b></dt>
<dd>

Use a global database option to override for a given statement.

```
<materialized_view_staleness_option> ::=
   { materialized_view_staleness_check = <materialized_view_staleness_check_value>
   | materialized_view_staleness_limit = <materialized_view_staleness_limit_value> }
```


<dl>
<dt><b>

*<materialized\_view\_staleness\_check\_value\>*

</b></dt>
<dd>

Specifies which type of materialized views are checked for staleness when read.


<dl>
<dt><b>

0 \(OFF\)

</b></dt>
<dd>

Materialized views are not checked for staleness when they are read.



</dd><dt><b>

1 \(Default\)

</b></dt>
<dd>

Only AUTO REFRESH materialized views are checked for staleness when they are read.



</dd><dt><b>

2

</b></dt>
<dd>

All materialized views are checked for staleness when they are read.



</dd>
</dl>



</dd><dt><b>

*<materialized\_view\_staleness\_limit\_value\>*

</b></dt>
<dd>

Specifies the maximum time a materialized view can be stale and still be read without error when materialized\_view\_staleness\_check is not equal to 0 \(OFF\).


<dl>
<dt><b>

Fresh

</b></dt>
<dd>

Use a materialized view only if it is fresh \(data in underlying tables has not been modified since the view was last refreshed\).



</dd><dt><b>

N \( \{ Minute\[s\] | Hour\[s\] | Day\[s\] | Week\[s\] | Month\[s\] \} \)

</b></dt>
<dd>

Use stale materialized views, as long as the stale materialized views have been refreshed within the specified time period. N is an integer greater than 0. A value of 1 week means 7 days and a value of 1 month means 30 days. Value cannot exceed 2<sup>31</sup> minutes. The default setting is 30 minutes.



</dd>
</dl>



</dd>
</dl>



</dd>
</dl>



<a name="loio7123f8b4e1f14a8f9efd257794202198__section_evn_w4w_brb"/>

## Remarks

You can use a SELECT statement in Interactive SQL to browse data in the database or to export data from the database to an external file.

You can also use a SELECT statement in procedures or in Embedded SQL. The SELECT statement with an INTO clause is used for retrieving results from the database when the SELECT statement returns only one row. \(Tables created with SELECT INTO do not inherit IDENTITY/AUTOINCREMENT tables.\) For multiple-row queries, you must use cursors. When you select more than one column and do not use *<\#table\>*, SELECT INTO creates a permanent base table. SELECT INTO *<\#table\>* always creates a temporary table regardless of the number of columns. SELECT INTO table with a single column selects into a host variable.

> ### Note:  
> When writing scripts and stored procedures that SELECT INTO a temporary table, wrap any select list item that is not a base column in a CAST expression. This guarantees that the column data type of the temporary table is the required data type.

Tables with the same name but different owners require aliases. A query without aliases returns incorrect results:

```
SELECT * FROM user1.t1
WHERE NOT EXISTS
(SELECT *
FROM user2.t1
WHERE user2.t1.col1 = user1.t1.col1);
```

For correct results, use an alias for each table:

```
SELECT * FROM user1.t1 U1
WHERE NOT EXISTS
(SELECT *
FROM user2.t1 U2
WHERE U2.col1 = U1.col1);
```

The INTO clause with a *<variable-list\>* is used only in procedures.

In SELECT statements, a stored procedure call can appear anywhere a base table or view is allowed. Note that CIS functional compensation performance considerations apply. For example, a SELECT statement can also return a result set from a procedure.



### The ROLLUP Operator

The ROLLUP operator requires an ordered list of grouping expressions to be supplied as arguments. ROLLUP first calculates the standard aggregate values specified in the GROUP BY. Then ROLLUP moves from right to left through the list of grouping columns and creates progressively higher-level subtotals. A grand total is created at the end. If *<n\>* is the number of grouping columns, ROLLUP creates *<n+1\>* levels of subtotals.

Restrictions on the ROLLUP operator:

-   ROLLUP supports all of the aggregate functions available to the GROUP BY clause, but ROLLUP does not currently support COUNT DISTINCT and SUM DISTINCT.
-   ROLLUP can be used only in the SELECT statement; you cannot use ROLLUP in a SELECT subquery.
-   A multiple grouping specification that combines ROLLUP, CUBE, and GROUP BY columns in the same GROUP BY clause is not currently supported.
-   Constant expressions as GROUP BY keys are not supported.

GROUPING is used with the ROLLUP operator to distinguish between stored NULL values and NULL values in query results created by ROLLUP.

ROLLUP syntax:

```
SELECT … [ GROUPING ( <column-name >) …] …
GROUP BY [ <expression> [, …]
| ROLLUP ( <expression> [, …] ) ]
```

GROUPING takes a column name as a parameter and returns a Boolean value:


<table>
<tr>
<th valign="top">

If the Value of the Result Is

</th>
<th valign="top">

GROUPING Returns

</th>
</tr>
<tr>
<td valign="top">

NULL created by a ROLLUP operation

</td>
<td valign="top">

1 \(TRUE\)

</td>
</tr>
<tr>
<td valign="top">

NULL indicating the row is a subtotal

</td>
<td valign="top">

1 \(TRUE\)

</td>
</tr>
<tr>
<td valign="top">

not created by a ROLLUP operation

</td>
<td valign="top">

0 \(FALSE\)

</td>
</tr>
<tr>
<td valign="top">

a stored NULL

</td>
<td valign="top">

0 \(FALSE\)

</td>
</tr>
</table>



### The CUBE Operator

Restrictions on the CUBE operator:

-   CUBE supports all of the aggregate functions available to the GROUP BY clause, but CUBE does not currently support COUNT DISTINCT or SUM DISTINCT.
-   CUBE does not currently support the inverse distribution analytical functions PERCENTILE\_CONT and PERCENTILE\_DISC.
-   CUBE can be used only in the SELECT statement; you cannot use CUBE in a SELECT subquery.
-   A multiple GROUPING specification that combines ROLLUP, CUBE, and GROUP BY columns in the same GROUP BY clause is not currently supported.
-   Constant expressions as GROUP BY keys are not supported.

GROUPING is used with the CUBE operator to distinguish between stored NULL values and NULL values in query results created by CUBE.

CUBE syntax:

```
SELECT … [ GROUPING ( <column-name> ) …] …
GROUP BY [ <expression> [, …]
| CUBE ( <expression> [, …] ) ]
```

GROUPING takes a column name as a parameter and returns a Boolean value:


<table>
<tr>
<th valign="top">

If the Value of the Result Is

</th>
<th valign="top">

GROUPING Returns

</th>
</tr>
<tr>
<td valign="top">

NULL created by a CUBE operation

</td>
<td valign="top">

1 \(TRUE\)

</td>
</tr>
<tr>
<td valign="top">

NULL indicating the row is a subtotal

</td>
<td valign="top">

1 \(TRUE\)

</td>
</tr>
<tr>
<td valign="top">

not created by a CUBE operation

</td>
<td valign="top">

0 \(FALSE\)

</td>
</tr>
<tr>
<td valign="top">

a stored NULL

</td>
<td valign="top">

0 \(FALSE\)

</td>
</tr>
</table>

When generating a query plan, the data lake Relational Engine optimizer estimates the total number of groups generated by the GROUP BY CUBE hash operation. The MAX\_CUBE\_RESULTS database option sets an upper boundary for the number of estimated rows the optimizer considers for a hash algorithm that can be run. If the actual number of rows exceeds the MAX\_CUBE\_RESULT option value, the optimizer stops processing the query and returns the error message "***Estimate number: nnn exceed the DEFAULT\_MAX\_CUBE\_RESULT of GROUP BY CUBE or ROLLUP***," where *<nnn\>* is the number estimated by the optimizer. See *MAX\_CUBE\_RESULT Option* for information on setting the MAX\_CUBE\_RESULT option.



### Unexpected Query Results

In a few unusual circumstances, differences in semantics between SQL Anywhere and data lake Relational Engine may produce unexpected query results. These circumstances are:

-   A query is issued from inside a user-defined function

-   A SELECT statement has no FROM clause

-   A FROM clause contains some tables that were created IN SYSTEM and others that were not created IN SYSTEM


In these circumstances, subtle differences between the semantics of SQL Anywhere and data lake Relational Engine may be exposed. These differences include:

-   Data lake Relational Engine treats the CHAR and VARCHAR data types as distinct and different; SQL Anywhere treats CHAR data as if it were VARCHAR.

-   When the RAND function is passed an argument, the behavior is deterministic in data lake Relational Engine and nondeterministic in SAP SQL Anywhere.




<a name="loio7123f8b4e1f14a8f9efd257794202198__section_kph_1yy_wwb"/>

## Privileges



### 


<dl>
<dt><b>

Connected to SAP HANA database as a SAP HANA database user.:

</b></dt>
<dd>

Requires one of:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the SAP HANA database REMOTE\_EXECUTE procedure associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).

-   See [REMOTE\_EXECUTE Guidance and Examples for Executing SQL Statements](remote-execute-guidance-and-examples-for-executing-sql-statements-fd99ac0.md).




</dd><dt><b>

Connected directly to data lake Relational Engine as a data lake Relational Engine user:

</b></dt>
<dd>

To SELECT from tables, views, and materialized views requires one of the following:

-   You own the object
-   SELECT ANY TABLE system privilege
-   SELECT object-level privilege on the object
-   SELECT object-level privilege on the schema containing the object if the schema is owned by another user.



</dd>
</dl>



<a name="loio7123f8b4e1f14a8f9efd257794202198__section_unq_dpw_brb"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products – supported by SAP Adaptive Server Enterprise, with some differences in syntax.



<a name="loio7123f8b4e1f14a8f9efd257794202198__section_nn2_2pw_brb"/>

## Examples

-   The following example lists all tables and views in the system catalog:

    ```
    SELECT tname
    FROM SYS.SYSCATALOG
    WHERE tname LIKE 'SYS%' ;
    ```

-   The following example lists all customers and the total value of their orders:

    ```
    SELECT CompanyName,
      CAST( sum(SalesOrderItems.Quantity *
      Products.UnitPrice) AS INTEGER) VALUE
    FROM Customers
      LEFT OUTER JOIN SalesOrders
      LEFT OUTER JOIN SalesOrderItems
      LEFT OUTER JOIN Products
    GROUP BY CompanyName
    ORDER BY VALUE DESC;
    ```

-   The following example lists the number of employees:

    ```
    SELECT count(*)
    FROM Employees;
    ```

-   The following example is an Embedded SQL SELECT statement:

    ```
    SELECT count(*) INTO :size FROM Employees;
    ```

-   The following example lists the total sales by year, model, and color:

    ```
    SELECT year, model, color, sum(sales) 
    FROM sales_tab 
    GROUP BY ROLLUP (year, model, color);
    ```

-   The following example selects all items with a certain discount into a temporary table:

    ```
    SELECT * INTO #TableTemp FROM lineitem 
    WHERE l_discount < 0.5;
    ```

-   The following example returns information about the employee that appears first when employees are sorted by last name:

    ```
    SELECT FIRST *
    FROM Employees
    ORDER BY Surname;
    ```

-   The following examples return the first five employees when their names are sorted by last name:

    ```
    SELECT TOP 5 *
    FROM Employees
    ORDER BY Surname;
    ```

    ```
    SELECT *
    FROM Employees
    ORDER BY Surname
    LIMIT 5;
    ```

-   The following example lists the fifth and sixth employees sorted in descending order by last name:

    ```
    SELECT *
    FROM Employees
    ORDER BY Surname DESC
    LIMIT 4,2;
    ```


**Related Information**  


[CREATE VIEW Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](create-view-statement-for-data-lake-relational-engine-sap-hana-db-managed-4d41128.md "Creates a view on the database. Views are used to give a different perspective on the data even though it is not stored that way.")

[LOAD TABLE Statement \(Non-Parquet Formats\) for Data Lake Relational Engine \(SAP HANA DB-Managed\)](load-table-statement-non-parquet-formats-for-data-lake-relational-engine-sap-hana-db-mana-97f011f.md "Imports data into a data lake Relational Engine database table from either the external object store (Azure BLOB storage, an Amazon S3 bucket, an S3-compliant bucket, or Google Cloud Storage) or from data lake Files containers (the managed object store).")

[SELECT Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a624e72e84f210159276a39335acd358.html "Retrieves information from the database.") :arrow_upper_right:

