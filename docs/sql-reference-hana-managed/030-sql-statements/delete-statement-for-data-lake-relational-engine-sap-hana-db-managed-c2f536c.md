<!-- loioc2f536c346c44911be3623014bc53910 -->

# DELETE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Deletes all the rows from the named table that satisfy the search condition. If no WHERE clause is specified, all rows from the named table are deleted.



## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:

-   Connected to SAP HANA database as a SAP HANA database user and using the SAP HANA database REMOTE\_EXECUTE procedure.



```
DELETE 
   [ FROM ] [ <schema-name>.]<table-name> [ [ AS <correlation-name> ]
   ...[ FROM <table-expression> ] 
   [ WHERE <search-condition> ] ]
```

```
<table-expression> ::=
   { <table-spec> 
   | <table-expression join-type table-spec> [ ON <condition> ] 
   | <table-expression>, ... };
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioc2f536c346c44911be3623014bc53910__section_jwf_vwg_1rb"/>

## Parameters


<dl>
<dt><b>

FROM clause

</b></dt>
<dd>

Indicates the table from which rows will be deleted. The optional second FROM clause in the DELETE statement determines the rows to be deleted from the specified table based on joins with other tables. If the second FROM clause is present, the WHERE clause qualifies the rows of this second FROM clause. Rows are deleted from the table name given in the first FROM clause.



</dd><dt><b>

WHERE clause

</b></dt>
<dd>

If specified, only rows satisfying the search condition are deleted. If no WHERE clause is specified, every row is deleted.



</dd>
</dl>



<a name="loioc2f536c346c44911be3623014bc53910__section_nmc_wwg_1rb"/>

## Remarks

DELETE can be used on views provided the SELECT statement defining the view has only one table in the FROM clause and does not contain a GROUP BY clause, an aggregate function, or involve a UNION operation.

If the same table name from which you are deleting rows is used in both FROM clauses, they are considered to reference the same table if one of the following is true:

-   Both table references are not qualified by specifying a user ID
-   Both table references are qualified by specifying a user ID
-   Both table references are specified with a correlation name

In cases where the server cannot determine if the table references are identical, an error appears. This prevents the user from unintended semantics by deleting unintended rows.



### Potential Ambiguity in Table Names

There is a potential ambiguity in table names in DELETE statements when the FROM clauses do not both use correlation names. Consider this example:

```
DELETE
FROM table_1
FROM table_1 AS alias_1, table_2 AS alias_2
WHERE ...;
```

table\_1 is identified without a correlation name in the first FROM clause, but with a correlation name in the second FROM clause. The use of a correlation name for table\_1 in the second FROM clause ensures that only one instance of table\_1 exists in the statement. This is an exception to the general rule that where the same table is identified with and without a correlation name in the same statement, two instances of the table are considered.

Now consider this example:

```
DELETE
FROM table_1
FROM table_1 AS alias_1, table_1 AS alias_2
WHERE ...;
```

There are two instances of table\_1 in the second FROM clause. Since there is no way to identify which instance the first FROM clause should be identified with, the general rule of correlation names means that table\_1 in the first FROM clause is identified with neither instance of table\_1 in the second clause: there are three instances of table\_1 in the statement.



<a name="loioc2f536c346c44911be3623014bc53910__section_dkr_2hx_wwb"/>

## Privileges



### 


<dl>
<dt><b>

Connected to SAP HANA database as a SAP HANA database user and using the SAP HANA database REMOTE\_EXECUTE procedure:

</b></dt>
<dd>

Requires one of:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the SAP HANA database REMOTE\_EXECUTE procedure associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).

-   See [REMOTE\_EXECUTE Guidance and Examples for Executing SQL Statements](remote-execute-guidance-and-examples-for-executing-sql-statements-fd99ac0.md).




</dd>
</dl>



<a name="loioc2f536c346c44911be3623014bc53910__section_pzd_xwg_1rb"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar.
-   SAP database products – supported by SAP Adaptive Server Enterprise, including the vendor extension.



<a name="loioc2f536c346c44911be3623014bc53910__section_nvp_xwg_1rb"/>

## Examples

-   The following example removes employee 105 from the database:

    ```
    DELETE
    FROM Employees
    WHERE EmployeeID = 105;
    ```

-   The following example removes all data prior to 1993 from the FinancialData table:

    ```
    DELETE
    FROM FinancialData
    WHERE Year < 1993;
    ```

-   The following example removes all names from the Contacts table if they are already present in the Customers table:

    ```
    DELETE
    FROM Contacts
    FROM Contacts, Customers
    WHERE Contacts.Surname = Customers.Surname
    AND Contacts.GivenName = Customers.GivenName;
    ```


**Related Information**  


[DELETE Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/a61b555884f21015bfb8d2d61d09b74c.html "Deletes all the rows from the named table that satisfy the search condition. If no WHERE clause is specified, all rows from the named table are deleted.") :arrow_upper_right:

