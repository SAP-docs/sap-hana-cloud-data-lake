<!-- loioa61b555884f21015bfb8d2d61d09b74c -->

# DELETE Statement for Data Lake Relational Engine

Deletes all the rows from the named table that satisfy the search condition. If no WHERE clause is specified, all rows from the named table are deleted.



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
DELETE 
   [ FROM ] [ { <owner> | <schema-name> }.]<table-name> [ [ AS <correlation-name> ]
   ...[ FROM <table-expression> ] 
   [ WHERE <search-condition> ] ]
```

```
<table-expression> ::=
   { <table-spec> 
   | <table-expression join-type table-spec> [ ON <condition> ] 
   | <table-expression>, ... }
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa61b555884f21015bfb8d2d61d09b74c__delete_parameters"/>

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



<a name="loioa61b555884f21015bfb8d2d61d09b74c__delete_remarks1"/>

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
WHERE ...
```

table\_1 is identified without a correlation name in the first FROM clause, but with a correlation name in the second FROM clause. The use of a correlation name for table\_1 in the second FROM clause ensures that only one instance of table\_1 exists in the statement. This is an exception to the general rule that where the same table is identified with and without a correlation name in the same statement, two instances of the table are considered.

Now consider this example:

```
DELETE
FROM table_1
FROM table_1 AS alias_1, table_1 AS alias_2
WHERE ...
```

There are two instances of table\_1 in the second FROM clause. Since there is no way to identify which instance the first FROM clause should be identified with, the general rule of correlation names means that table\_1 in the first FROM clause is identified with neither instance of table\_1 in the second clause: there are three instances of table\_1 in the statement.



<a name="loioa61b555884f21015bfb8d2d61d09b74c__delete_privileges1"/>

## Privileges



### 

To DELETE tables and views requires one of:

-   You own the object
-   DELETE ANY TABLE system privilege
-   DELETE object-level privilege on the object
-   DELETE object-level privilege on the schema containing the object if the schema is owned by another user.

See [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md) for assistance with granting privileges



<a name="loioa61b555884f21015bfb8d2d61d09b74c__delete_standards1"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar.
-   SAP database products – supported by SAP Adaptive Server Enterprise, including the vendor extension.



<a name="loioa61b555884f21015bfb8d2d61d09b74c__delete_examples1"/>

## Examples

-   The following example removes employee 105 from the database:

    ```
    DELETE
    FROM Employees
    WHERE EmployeeID = 105
    ```

-   The following example removes all data prior to 1993 from the FinancialData table:

    ```
    DELETE
    FROM FinancialData
    WHERE Year < 1993
    ```

-   The following example removes all names from the Contacts table if they are already present in the Customers table:

    ```
    DELETE
    FROM Contacts
    FROM Contacts, Customers
    WHERE Contacts.Surname = Customers.Surname
    AND Contacts.GivenName = Customers.GivenName
    ```


**Related Information**  


[FROM Clause for Data Lake Relational Engine](from-clause-for-data-lake-relational-engine-a7749cf.md "Specifies the database tables or views involved in a SELECT statement.")

[INSERT Statement for Data Lake Relational Engine](insert-statement-for-data-lake-relational-engine-a61fdef.md "Inserts a single row or a selection of rows, from elsewhere in the current database, into the table. This command can also insert a selection of rows from another database into the table.")

[TRUNCATE Statement for Data Lake Relational Engine](truncate-statement-for-data-lake-relational-engine-a627e60.md "Deletes all rows from a table or materialized view without deleting the table definition.")

[DELETE Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/c2f536c346c44911be3623014bc53910.html "Deletes all the rows from the named table that satisfy the search condition. If no WHERE clause is specified, all rows from the named table are deleted.") :arrow_upper_right:

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[REVOKE Object-Level Privilege Statement for Data Lake Relational Engine](revoke-object-level-privilege-statement-for-data-lake-relational-engine-a3e7af2.md "Removes object-level privileges that were given using the GRANT statement.")

