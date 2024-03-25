<!-- loioa61a051684f210158cced2d83231bd8a -->

# CREATE VIEW Statement for Data Lake Relational Engine 

Creates a view on the database. Views are used to give a different perspective on the data even though it is not stored that way.



<a name="loioa61a051684f210158cced2d83231bd8a__section_azh_5fj_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
CREATE [ OR REPLACE ] VIEW
   [ { <owner> | <schema-name> }.]<view-name> [ ( <column-name> [ , … ] ) ]
   AS <select-statement>
   [ WITH CHECK OPTION ]
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa61a051684f210158cced2d83231bd8a__create_view_parameters1"/>

## Parameters


<dl>
<dt><b>

OR REPLACE

</b></dt>
<dd>

Replaces an existing view with the same name. Existing permissions are preserved , but INSTEAD OF triggers on the view are dropped.



</dd><dt><b>

*<view-name\>*

</b></dt>
<dd>

The default owner of a view is the current user ID. A view name can be used in place of a table name in SELECT, DELETE, UPDATE, and INSERT statements. Views, however, do not physically exist in the database as tables. They are derived each time they are used. The view is derived as the result of the SELECT statement specified in the CREATE VIEW statement. Table names used in a view should be qualified by the user ID of the table owner. Otherwise, a different user ID might not be able to find the table or might get the wrong table.



</dd><dt><b>

AS *<select-statement\>*

</b></dt>
<dd>

The SELECT statement on which the view is based must not contain an ORDER BY clause, a subquery in the SELECT list, or a TOP or FIRST qualification. It may have a GROUP BY clause and may be a UNION.



</dd><dt><b>

WITH CHECK OPTION

</b></dt>
<dd>

Rejects any updates and inserts to the view that do not meet the criteria of the views as defined by its SELECT statement. However, data lake Relational Engine currently ignores this option \(it supports the syntax for compatibility reasons\).



</dd>
</dl>



<a name="loioa61a051684f210158cced2d83231bd8a__create_view_remarks1"/>

## Remarks

You cannot add or drop IDENTITY or AUTOINCREMENT columns from a view.

Views can be updated unless the SELECT statement defining the view contains a GROUP BY clause, an aggregate function, or involves a UNION operation. An update to the view causes the underlying tables to be updated.



<a name="loioa61a051684f210158cced2d83231bd8a__create_view_privileges1"/>

## Privileges



### 

There are two parts to the privileges required to create a view. Part 1 are the privileges to create the view. Part 2 is the privileges to select from the underlying object of the view.

Part 1: Privileges for the view:

-   To create a self-owned view requires one of:
    -   CREATE VIEW system privilege
    -   CREATE ANY VIEW system privilege
    -   CREATE ANY OBJECT system privilege

-   To create a view owned by another user requires one of:
    -   CREATE ANY VIEW system privilege
    -   CREATE ANY OBJECT system privilege
    -   CREATE ANY object-level privilege on the schema to contain the view if the schema is owned by another user.


Part 2: Privileges for the underlying objects of the view:

-   If the object is self-owned, then no additional privilege is needed.
-   If the object is owned by another user, then you need one of:
    -   SELECT object-level privilege on the referenced objects.
    -   SELECT ANY TABLE system privilege.
    -   SELECT object-level privilege on the schema containing the referenced objects if the schema is owned by another user.


See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) or [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md) for assistance with granting privileges.



<a name="loioa61a051684f210158cced2d83231bd8a__create_view_side_effects1"/>

## Side Effects

Automatic commit



<a name="loioa61a051684f210158cced2d83231bd8a__create_view_standards1"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   



<a name="loioa61a051684f210158cced2d83231bd8a__create_view_examples1"/>

## Examples

-   The following example creates a view showing all information for male employees only. This view has the same column names as the base table:

    ```
    CREATE VIEW male_employee
    AS SELECT *
    FROM Employees
    WHERE Sex = 'M';
    ```

-   The following example creates a view showing employees and the departments to which they belong:

    ```
    CREATE VIEW emp_dept
    AS SELECT Surname, GivenName, DepartmentName
    FROM Employees JOIN Departments
    ON Employees.DepartmentID = Departments.DepartmentID;
    ```


**Related Information**  


[ALTER VIEW Statement for Data Lake Relational Engine](alter-view-statement-for-data-lake-relational-engine-a613cd2.md "Replaces a view definition with a modified version.")

[DROP VIEW Statement for Data Lake Relational Engine](drop-view-statement-for-data-lake-relational-engine-10a78b1.md "Removes a view from the database.")

[CREATE TABLE Statement for Data Lake Relational Engine](create-table-statement-for-data-lake-relational-engine-a619764.md "Creates a new table in the database or on a remote server.")

[SELECT Statement for Data Lake Relational Engine](select-statement-for-data-lake-relational-engine-a624e72.md "Retrieves information from the database.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[REVOKE Object-Level Privilege Statement for Data Lake Relational Engine](revoke-object-level-privilege-statement-for-data-lake-relational-engine-a3e7af2.md "Removes object-level privileges that were given using the GRANT statement.")

[CREATE VIEW Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/4d411288dcae4da3a64d44865a0574e9.html "Creates a view on the database. Views are used to give a different perspective on the data even though it is not stored that way.") :arrow_upper_right:

