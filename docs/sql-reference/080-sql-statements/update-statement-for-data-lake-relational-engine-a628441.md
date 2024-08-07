<!-- loioa628441e84f21015a952a4b8bd52ee72 -->

# UPDATE Statement for Data Lake Relational Engine

Modifies existing rows of a single table, or a view that contains only one table.



<a name="loioa628441e84f21015a952a4b8bd52ee72__section_azh_5fj_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
UPDATE [ { <owner> | <schema-name> }.]{ <table-name> | <view-name> } [ [ AS ] <correlation-name> ]
   ...SET [ <update-clause> [,...] ]
```

```
<update-clause> ::=
   ...<column-expression>
   ...[ FROM <table-expression> ] 
   ...[ WHERE <search-condition> ]
   ...[ ORDER BY <expression> [ { ASC | DESC } ]

```

```
<column-expression>
   <column-name> = <expression> [,...]
```

```
<table-expression> ::=
   <table-spec> 
   | <table-expression> <join-type> <table-spec> [ ON <condition> ] 
   | <table-expression>, ...
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa628441e84f21015a952a4b8bd52ee72__update_parameters1"/>

## Parameters


<dl>
<dt><b>

SET

</b></dt>
<dd>

Use the SET clause to set column names or variables to the specified expression.

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



</dd><dt><b>

FROM

</b></dt>
<dd>

Allows tables to be updated based on joins. If the FROM clause is present, *<table-name\>* must specify the sole table to be updated, and it must qualify the name in the same way as it appears in the FROM clause. If correlation names are used in the FROM clause, the identical correlation name must be specified as *<table-name\>*.

This statement illustrates a potential ambiguity in table names in UPDATE statements using a FROM clause that contain table expressions, which use correlation names:

```
UPDATE table_1
SET column_1 = ...
FROM table_1 AS alias_1, table_2 AS alias_2
WHERE ...;
```

Each instance of table\_1 in the FROM clause has a correlation name, denoting a self-join of table\_1 to itself. However, the UPDATE statement fails to specify which of the rows that make up the self-join are to be updated. This can be corrected by specifying the correlation name in the UPDATE statement as follows:

```
UPDATE table_1
SET column_1 = ...
FROM table_1 AS alias_1, table_1 AS alias_2
WHERE ...;
```

If the same table name in which you are updating rows is used in the FROM clause, they are considered to reference the same table if one of the following is true:

-   Both table references are not qualified by specifying a user ID
-   Both table references are qualified by specifying a user ID
-   Both table references are specified with a correlation name

In cases where the server cannot determine if the table references are identical, a SQL error appears. This prevents the user from unintended semantics by updating unintended rows.



</dd><dt><b>

WHERE clause

</b></dt>
<dd>

If specified, only rows satisfying the search condition are updated. If no WHERE clause is specified, every row is updated.



</dd><dt><b>

ORDER BY clause

</b></dt>
<dd>

Normally, the order in which rows are updated does not matter. However, with the FIRST or TOP clause, the order can be significant.

You cannot use ordinal column numbers in the ORDER BY clause.

To use the ORDER BY clause, you cannot set the ansi\_update\_constraints option to Strict.

To update columns that appear in the ORDER BY clause, set the ansi\_update\_constraints option to Off.



</dd>
</dl>



<a name="loioa628441e84f21015a952a4b8bd52ee72__update_remarks1"/>

## Remarks

The table referenced in the UPDATE statement can be a base table or a temporary table.

In data lake Relational Engine, a timestamp data type column can support 6 or 7 decimal precision. See [TIMESTAMP Data Type Precision in Data Lake Relational Engine](../020-sql-data-types/timestamp-data-type-precision-in-data-lake-relational-engine-520ce6c.md). If you attempt to insert 7 decimal precision data into a 6 decimal precision column in the data lake Relational Engine, then the value will be truncated to 6 decimal places and precision is lost. To prevent this behavior, set the TIMESTAMP\_RTRUNCATION database option to ON. See [TIMESTAMP\_RTRUNCATION Option for Data Lake Relational Engine](../090-database-options/timestamp-rtruncation-option-for-data-lake-relational-engine-dbb08c7.md).When enabled, the UPDATE operation fails if precision will be lost on a timestamp column.

Defaults on updates are honored for current user, user and current timestamp, and timestamp only.

Each named column is set to the value of the expression on the right-hand side of the equal sign. Even *<column-name\>* can be used in the expression—the old value is used.

The FROM clause can contain multiple tables with join conditions and returns all the columns from all the tables specified and filtered by the join condition and/or WHERE condition.

Using the wrong join condition in a FROM clause causes unpredictable results. If the FROM clause specifies a one-to-many join and the SET clause references a cell from the “many” side of the join, the cell is updated from the first value selected. In other words, if the join condition causes multiple rows of the table to be updated per row ID, the first row returned becomes the update result. For example:

```
UPDATE T1 
SET T1.c2 = T2.c2
FROM T1 JOIN TO T2
ON T1.c1 = T2.c1;
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
ON T1.rowid = T2.rowid;
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
WHERE r.a = 10;
```

Data lake Relational Engine supports DEFAULT column values in UPDATE statements. If a column has a DEFAULT value, this DEFAULT value is used as the value of the column in any UPDATE statement that does not explicitly modify the value for the column.

See *CREATE TABLE Statement* for details about updating IDENTITY/AUTOINCREMENT columns, which are another type of DEFAULT column.

When updating database-scope variables using the SET clause, the setting does not persist between restarts of the database, even though the variable does. When a database is restarted, the value of a database-scope variable reverts to NULL or its default, if defined. The SYSDATABASEVARIABLE system view contains a list of all database-scope variables and their default values.

You cannot update a database-scope variable owned by another user.



<a name="loioa628441e84f21015a952a4b8bd52ee72__update_privileges1"/>

## Privileges



### 

To UPDATE tables and views requires one of:

-   You own the object
-   UPDATE ANY TABLE system privilege
-   UPDATE object-level privilege on the column being modified
-   UPDATE object-level privilege on the schema containing the object if the schema is owned by another user.

No privileges are required to update a database-scope variable you own. To update a database-scope variable owned by PUBLIC, requires the UPDATE PUBLIC DATABASE VARIABLE system privilege.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) or [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md) for assistance with granting privileges.



<a name="loioa628441e84f21015a952a4b8bd52ee72__update_standards1"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar

-   SAP database products – with these exceptions, syntax of the IQ UPDATE statement is generally compatible with the SAP Adaptive Server Enterprise UPDATE statement. Syntax 1: data lake Relational Engine supports multiple tables with join conditions in the FROM clause.

    Updates of remote tables are limited to data lake Relational Engine syntax supported by CIS.




<a name="loioa628441e84f21015a952a4b8bd52ee72__update_examples1"/>

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


[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[CREATE TABLE Statement for Data Lake Relational Engine](create-table-statement-for-data-lake-relational-engine-a619764.md "Creates a new table in the database or on a remote server.")

[REVOKE Object-Level Privilege Statement for Data Lake Relational Engine](revoke-object-level-privilege-statement-for-data-lake-relational-engine-a3e7af2.md "Removes object-level privileges that were given using the GRANT statement.")

[TIMESTAMP Data Type Precision in Data Lake Relational Engine](../020-sql-data-types/timestamp-data-type-precision-in-data-lake-relational-engine-520ce6c.md "Precision conflicts between TIMESTAMP data types result in data loss.")

[UPDATE Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/2de4f7ac0a4244d597b33cb572ca1d8f.html "Modifies existing rows of a single table, or a view that contains only one table.") :arrow_upper_right:

[TIMESTAMP\_RTRUNCATION Option for Data Lake Relational Engine](../090-database-options/timestamp-rtruncation-option-for-data-lake-relational-engine-dbb08c7.md "Controls whether INSERT, UPDATE, or CAST operations on TIMESTAMP data type columns fails if loss of precision will result.")

