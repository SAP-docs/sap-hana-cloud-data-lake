<!-- loioa628143c84f21015866a8b40c421ead0 -->

# UNION Statement for Data Lake Relational Engine

Combines the results of two or more select statements.



<a name="loioa628143c84f21015866a8b40c421ead0__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
<select-without>-<order-by>
   … UNION [ ALL ] <select-without>-<order-by>
   … [ UNION [ ALL ] <select-without>-<order-by> ]…
   … [ <order-by-clause> [, ...] ]
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa628143c84f21015866a8b40c421ead0__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

ALL

</b></dt>
<dd>

The results of UNION ALL are the combined results of the component `SELECT` statements. The results of UNION are the same as UNION ALL, except that duplicate rows are eliminated. Eliminating duplicates requires extra processing, so UNION ALL should be used instead of UNION where possible.



</dd><dt><b>

*<order-by-clause\>*

</b></dt>
<dd>

Only integers are allowed in the order by list. These integers specify the position of the columns to be sorted.

```
<order-by-clause> ::=
   ORDER BY <integer> [ { ASC | DESC } ];
```



</dd>
</dl>



<a name="loioa628143c84f21015866a8b40c421ead0__IQ_Usage"/>

## Remarks

The results of several `SELECT` statements can be combined into a larger result using a UNION clause. The component `SELECT` statements must each have the same number of items in the select list, and cannot contain an ORDER BY clause. See *FROM Clause*.

If corresponding items in two select lists have different data types, data lake Relational Engine chooses a data type for the corresponding column in the result, and automatically converts the columns in each component `SELECT` statement appropriately.

The column names displayed are the same column names that display for the first `SELECT` statement.

> ### Note:  
> When `SELECT``iq_dummy` to avoid errors. See statements include constant values and UNION ALL views but omit the FROM clause, use *FROM Clause* for details.



<a name="loioa628143c84f21015866a8b40c421ead0__IQ_Permissions"/>

## Privileges

Requires SELECT object-level privilege for each object of the `SELECT` statements.

See [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md) for assistance with granting privileges



<a name="loioa628143c84f21015866a8b40c421ead0__IQ_Standards"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products – supported by SAP Adaptive Server Enterprise statements include constant values and, which also supports a COMPUTE clause.



<a name="loioa628143c84f21015866a8b40c421ead0__IQ_Examples"/>

## Examples

This example lists all distinct surnames of employees and customers:

```
SELECT Surname
FROM Employees
UNION
SELECT Surname
FROM Customers;
```

**Related Information**  


[REVOKE Object-Level Privilege Statement for Data Lake Relational Engine](revoke-object-level-privilege-statement-for-data-lake-relational-engine-a3e7af2.md "Removes object-level privileges that were given using the GRANT statement.")

[FROM Clause for Data Lake Relational Engine](from-clause-for-data-lake-relational-engine-a7749cf.md "Specifies the database tables or views involved in a SELECT statement.")

[SELECT Statement for Data Lake Relational Engine](select-statement-for-data-lake-relational-engine-a624e72.md "Retrieves information from the database.")

