<!-- loio2de4f7ac0a4244d597b33cb572ca1d8f -->

# UPDATE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Modifies existing rows of a single table, or a view that contains only one table.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Executing SQL Statements](remote-execute-usage-examples-for-executing-sql-statements-fd99ac0.md).



```
UPDATE [ [/pandoc/div/div/horizontalrule/codeblock/span/span
     {""}) [/pandoc/div/div/horizontalrule/codeblock/span/span/varname
     {"varname"}) <schema-name> (varname] (span].]{ [/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <table-name> (varname] | [/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <view-name> (varname] } [ [ AS ] [/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <correlation-name> (varname] ]
   ...SET [ [/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <update-clause> (varname] [,...] ]
```

```
[/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <update-clause> (varname] ::=
   ...[/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <column-expression> (varname]
   ...[ FROM [/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <table-expression> (varname] ] 
   ...[ WHERE [/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <search-condition> (varname] ]
   ...[ ORDER BY [/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <expression> (varname] [ { ASC | DESC } ]

```

```
[/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <column-expression> (varname]
   [/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <column-name> (varname] = [/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <expression> (varname] [,...]
```

```
<table-expression> ::=
   <table-spec> 
   | <table-expression> <join-type> <table-spec> [ ON <condition> ] 
   | <table-expression>, ...
```



<a name="loio2de4f7ac0a4244d597b33cb572ca1d8f__section_h3n_xdy_brb"/>

## Parameters

 SET
 :   Use the SET clause to set column names or variables to the specified expression.

    Use the SET clause to set the column to a computed column value by using this format:

    ```
    SET <column-name> = <expression>, ...
    ```

    Each specified column is set to the value of the expression. There are no restrictions on *<expression\>*. If *<expression\>* is a *<column-name\>*, then the previous value from that column is used.

    If a column has a default defined, then use the SET clause to set a column to its default value.

    You can also use the SET clause to assign a variable by using the following format:

    ```
    SET @<variable-name> = <expression>, ...
    ```

    The *<owner\>* specification is only for use with database-scope variables.

    When assigning a value to a variable, the variable must already be declared, and its name must begin with the at sign \(@\). If the variable name matches the name of a column in the table to be updated, then the UPDATE statement updates the column value and leaves the variable unchanged. Variable and column assignments can be combined in any order.

  FROM
 :   Allows tables to be updated based on joins. If the FROM clause is present, *<table-name\>* must specify the sole table to be updated, and it must qualify the name in the same way as it appears in the FROM clause. If correlation names are used in the FROM clause, the identical correlation name must be specified as *<table-name\>*.

    This statement illustrates a potential ambiguity in table names in UPDATE statements using a FROM clause that contain table expressions, which use correlation names:

    ```
    UPDATE table_1
    SET column_1 = ...
    FROM table_1 AS alias_1, table_2 AS alias_2
    WHERE ...
    ```

    Each instance of table\_1 in the FROM clause has a correlation name, denoting a self-join of table\_1 to itself. However, the UPDATE statement fails to specify which of the rows that make up the self-join are to be updated. This can be corrected by specifying the correlation name in the UPDATE statement as follows:

    ```
    UPDATE table_1
    SET column_1 = ...
    FROM table_1 AS alias_1, table_1 AS alias_2
    WHERE ...
    ```

    If the same table name in which you are updating rows is used in the FROM clause, they are considered to reference the same table if one of the following is true:

    -   Both table references are not qualified by specifying a user ID
    -   Both table references are qualified by specifying a user ID
    -   Both table references are specified with a correlation name

    In cases where the server cannot determine if the table references are identical, a SQL error appears. This prevents the user from unintended semantics by updating unintended rows.

  WHERE clause
 :   If specified, only rows satisfying the search condition are updated. If no WHERE clause is specified, every row is updated.

  ORDER BY clause
 :   Normally, the order in which rows are updated does not matter. However, with the FIRST or TOP clause, the order can be significant.

    You cannot use ordinal column numbers in the ORDER BY clause.

    To use the ORDER BY clause, you cannot set the ansi\_update\_constraints option to Strict.

    To update columns that appear in the ORDER BY clause, set the ansi\_update\_constraints option to Off.

 

<a name="loio2de4f7ac0a4244d597b33cb572ca1d8f__section_vd2_ydy_brb"/>

## Remarks

The table referenced in the UPDATE statement can be a base table or a temporary table.

Defaults on updates are honored for current user, user and current timestamp, and timestamp only.

Each named column is set to the value of the expression on the right-hand side of the equal sign. Even *<column-name\>* can be used in the expression—the old value is used.

The FROM clause can contain multiple tables with join conditions and returns all the columns from all the tables specified and filtered by the join condition and/or WHERE condition.

Using the wrong join condition in a FROM clause causes unpredictable results. If the FROM clause specifies a one-to-many join and the SET clause references a cell from the “many” side of the join, the cell is updated from the first value selected. In other words, if the join condition causes multiple rows of the table to be updated per row ID, the first row returned becomes the update result. For example:

```
UPDATE T1 
SET T1.c2 = T2.c2
FROM T1 JOIN TO T2
ON T1.c1 = T2.c1
```

If table T2 has more than one row per T2.c1, results might be as follows:

```
T2.c1              T2.c2              T2.c3
1                  4                  3
1                  8                  1
1                  6                  4
1                  5                  2
```

-   With no ORDER BY clause, T1.c2 may be 4, 5, 6, 8.
-   With ORDER BY T2.c3, T1.c2 is updated to 8.
-   With ORDER BY T2.c3 DESC, T1.c2 is updated to 6.

Data lake Relational Engine rejects any UPDATE statement in which the table being updated is on the null-supplying side of an outer join. In other words:

-   In a left outer join, the table on the left side of the join cannot be missing any rows on joined columns.
-   In a right outer join, the table on the right side of the join cannot be missing any rows on joined columns.
-   In a full outer join, neither table can be missing any rows on joined columns.

For example, in this statement, table T1 is on the left side of a left outer join, and thus cannot contain be missing any rows:

```
UPDATE T1 
SET T1.c2 = T2.c4
FROM T1 LEFT OUTER JOIN T2
ON T1.rowid = T2.rowid
```

Normally, the order in which rows are updated does not matter. However, in conjunction with the NUMBER\(\*\) function, an ordering can be useful to get increasing numbers added to the rows in some specified order. If you are not using the NUMBER\(\*\) function, avoid using the ORDER BY clause, because the UPDATE statement performs better without it.

In an UPDATE statement, if the NUMBER\(\*\) function is used in the SET clause and the FROM clause specifies a one-to-many join, NUMBER\(\*\) generates unique numbers that increase, but do not increment sequentially due to row elimination.

You can use the ORDER BY clause to control the result from an UPDATE statement when the FROM clause contains multiple joined tables.

Data lake Relational Engine ignores the ORDER BY clause in the UPDATE statement and returns a message that the syntax is not valid ANSI syntax.

The left side of each SET clause must be a column in a base table.

Views can be updated provided the SELECT statement defining the view does not contain a GROUP BY clause or an aggregate function, or involve a UNION operation. The view should contain only one table.

Character strings inserted into tables are always stored in the case they are entered, regardless of whether the database is case-sensitive or not. Thus a character data type column updated with the string 'Value' is always held in the database with an uppercase V and the remainder of the letters lowercase. SELECT statements return the string as 'Value.' If the database is not case-sensitive, however, all comparisons make 'Value' the same as 'value,' 'VALUE,' and so on. The IQ server may return results in any combination of lowercase and uppercase, so you cannot expect case-sensitive results in a database that is case-insensitive \(CASE IGNORE\). Further, if a single-column primary key already contains an entry 'Value,' an INSERT of 'value' is rejected, as it would make the primary key not unique.

If the update violates any check constraints, the whole statement is rolled back.

Data lake Relational Engine supports scalar subqueries within the SET clause, for example:

```
UPDATE r
SET r.o= (SELECT MAX(t.o) 
FROM t ... WHERE t.y = r.y),
r.s= (SELECT SUM(x.s) 
FROM x ... 
WHERE x.x = r.x)
WHERE r.a = 10
```

Data lake Relational Engine supports DEFAULT column values in UPDATE statements. If a column has a DEFAULT value, this DEFAULT value is used as the value of the column in any UPDATE statement that does not explicitly modify the value for the column.

See *CREATE TABLE Statement* for details about updating IDENTITY/AUTOINCREMENT columns, which are another type of DEFAULT column.

When updating database-scope variables using the SET clause, the setting does not persist between restarts of the database, even though the variable does. When a database is restarted, the value of a database-scope variable reverts to NULL or its default, if defined. The SYSDATABASEVARIABLE system view contains a list of all database-scope variables and their default values.

You cannot update a database-scope variable owned by another user.



<a name="loio2de4f7ac0a4244d597b33cb572ca1d8f__section_iyf_2bz_wwb"/>

## Privileges



### 

You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loio2de4f7ac0a4244d597b33cb572ca1d8f__section_imw_22y_brb"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar

-   SAP database products – with these exceptions, syntax of the IQ UPDATE statement is generally compatible with the SAP Adaptive Server Enterprise UPDATE statement. Syntax 1: data lake Relational Engine supports multiple tables with join conditions in the FROM clause.

    Updates of remote tables are limited to data lake Relational Engine syntax supported by CIS.




<a name="loio2de4f7ac0a4244d597b33cb572ca1d8f__section_d3m_f2y_brb"/>

## Examples

-   This example transfers employee Philip Chin \(employee 129\) from the sales department to the marketing department:

    ```
    UPDATE Employees
    SET DepartmentID = 400
    WHERE EmployeeID = 129;
    ```

-   In this example, the Marketing Department \(400\) increases bonuses from 4% to 6% of each employee’s base salary:

    ```
    UPDATE Employees
    SET bonus = base * 6/100
    WHERE DepartmentID =400;
    ```

-   In this example, each employee gets a pay increase with the department bonus:

    ```
    UPDATE Employees
    SET emp.Salary = emp.Salary + dept.bonus
    FROM Employees emp, Departments dept
    WHERE emp.DepartmentID = dept.DepartmentID;
    ```

-   This example shows another way to give each employee a pay increase with the department bonus:

    ```
    UPDATE Employees
    SET emp.salary = emp.salary + dept.bonus
    FROM Employees emp JOIN Departments dept
    ON emp.DepartmentID = dept.DepartmentID;
    ```


**Related Information**  


[UPDATE Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a628441e84f21015a952a4b8bd52ee72.html "Modifies existing rows of a single table, or a view that contains only one table.") :arrow_upper_right:

