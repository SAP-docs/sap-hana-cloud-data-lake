<!-- loio4d411288dcae4da3a64d44865a0574e9 -->

# CREATE VIEW Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Creates a view on the database. Views are used to give a different perspective on the data even though it is not stored that way.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Executing SQL Statements](remote-execute-usage-examples-for-executing-sql-statements-fd99ac0.md).



```
CREATE [ OR REPLACE ] VIEW
   [ [/pandoc/div/div/horizontalrule/codeblock/span/span
     {""}) [/pandoc/div/div/horizontalrule/codeblock/span/span/varname
     {"varname"}) <schema-name> (varname] (span].][/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <view-name> (varname] [ ( [/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <column-name> (varname] [ , … ] ) ]
   AS [/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <select-statement> (varname]
   [ WITH CHECK OPTION ]
```



<a name="loio4d411288dcae4da3a64d44865a0574e9__section_odh_cwg_1rb"/>

## Parameters

 OR REPLACE
 :   Replaces an existing view with the same name. Existing permissions are preserved , but INSTEAD OF triggers on the view are dropped.

  *<view-name\>*
 :   The default owner of a view is the current user ID. A view name can be used in place of a table name in SELECT, DELETE, UPDATE, and INSERT statements. Views, however, do not physically exist in the database as tables. They are derived each time they are used. The view is derived as the result of the SELECT statement specified in the CREATE VIEW statement. Table names used in a view should be qualified by the user ID of the table owner. Otherwise, a different user ID might not be able to find the table or might get the wrong table.

  AS *<select-statement\>*
 :   The SELECT statement on which the view is based must not contain an ORDER BY clause, a subquery in the SELECT list, or a TOP or FIRST qualification. It may have a GROUP BY clause and may be a UNION.

  WITH CHECK OPTION
 :   Rejects any updates and inserts to the view that do not meet the criteria of the views as defined by its SELECT statement. However, data lake Relational Engine currently ignores this option \(it supports the syntax for compatibility reasons\).

 

<a name="loio4d411288dcae4da3a64d44865a0574e9__section_wlz_cwg_1rb"/>

## Remarks

You cannot add or drop IDENTITY or AUTOINCREMENT columns from a view.

Views can be updated unless the SELECT statement defining the view contains a GROUP BY clause, an aggregate function, or involves a UNION operation. An update to the view causes the underlying tables to be updated.



<a name="loio4d411288dcae4da3a64d44865a0574e9__section_ut5_rfs_wwb"/>

## Privileges



### 

You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loio4d411288dcae4da3a64d44865a0574e9__section_jwg_2wg_1rb"/>

## Side Effects

Automatic commit



<a name="loio4d411288dcae4da3a64d44865a0574e9__section_yrq_2wg_1rb"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   



<a name="loio4d411288dcae4da3a64d44865a0574e9__section_d5f_fwg_1rb"/>

## Examples

-   The following example creates a view showing all information for male employees only. This view has the same column names as the base table:

    ```
    CREATE VIEW male_employee
    AS SELECT *
    FROM Employees
    WHERE Sex = 'M'
    ```

-   The following example creates a view showing employees and the departments to which they belong:

    ```
    CREATE VIEW emp_dept
    AS SELECT Surname, GivenName, DepartmentName
    FROM Employees JOIN Departments
    ON Employees.DepartmentID = Departments.DepartmentID
    ```


**Related Information**  


[ALTER VIEW Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](alter-view-statement-for-data-lake-relational-engine-sap-hana-db-managed-6ef5483.md "Replaces a view definition with a modified version.")

[System Views in Data Lake Relational Engine \(SAP HANA DB-Managed\)](../070-system-views/system-views-in-data-lake-relational-engine-sap-hana-db-managed-92e2e6c.md "System views allow you to query for information about the system state using SELECT statements. The results appear as tables.")

[DROP Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](drop-statement-for-data-lake-relational-engine-sap-hana-db-managed-367d71d.md "Removes objects from the database.")

[CREATE VIEW Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a61a051684f210158cced2d83231bd8a.html "Creates a view on the database. Views are used to give a different perspective on the data even though it is not stored that way.") :arrow_upper_right:

