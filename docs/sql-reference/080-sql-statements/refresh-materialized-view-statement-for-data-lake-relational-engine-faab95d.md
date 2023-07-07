<!-- loiofaab95d872784a4c8d2a7bd3e74faa04 -->

# REFRESH MATERIALIZED VIEW Statement for Data Lake Relational Engine

Initializes or refreshes the data in a materialized view by executing its query definition.



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
REFRESH MATERIALIZED VIEW [ { <owner> | <schema-name>}.]<mat_view_name>
   [ FORCE BUILD ]
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loiofaab95d872784a4c8d2a7bd3e74faa04__refresh_matview_parameters1"/>

## Parameters


<dl class="glossary">
<dt><b>

FORCE BUILD

</b></dt>
<dd>

By default, when you execute a REFRESH MATERIALIZED VIEW statement, the database server checks whether the materialized view is stale \(that is, underlying tables have changed since the materialized view was last refreshed\). If it is not stale, the refresh does not take place. Specify the FORCE BUILD clause to force a refresh of the materialized view regardless of whether the materialized view is stale.



</dd>
</dl>



<a name="loiofaab95d872784a4c8d2a7bd3e74faa04__refresh_matview_remarks1"/>

## Remarks

Use this statement to initialize or refresh the materialized view.

If a REFRESH MATERIALIZED VIEW statement is executed against a materialized view that is not stale, a refresh is not performed unless the FORCE BUILD clause is specified.

This statement cannot be executed when the connection has cursors opened with the WITH HOLD clause that use either statement or transaction snapshots.



<a name="loiofaab95d872784a4c8d2a7bd3e74faa04__refresh_mat_view_privileges1"/>

## Privileges



### 

Requires one of:

-   You own the materialized view.
-   INSERT object-level privilege on the materialized view
-   INSERT object-level privilege on the schema containing the materialized view if the schema is owned by another user.

Additionally, requires one of:

-   You own the underlying tables of the materialized view
-   SELECT ANY TABLE system privilege
-   SELECT object-level privilege on the underlying tables
-   SELECT object-level privilege on the schema containing the underlying tables of the materialized view if the schema is owned by another user.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) or [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md) for assistance with granting privileges.



<a name="loiofaab95d872784a4c8d2a7bd3e74faa04__refresh_matview_side_effects1"/>

## Side Effects

A refresh of a materialized view fails if there is an open cursor because the exclusive locks cannot be acquired.

A checkpoint is performed at the beginning of execution.

Automatic commits are performed at the beginning and end of execution.

While executing, an exclusive schema lock is placed on the materialized view being refreshed using the connection blocking option, and shared schema locks, without blocking, are placed on all tables referenced by the materialized view. Also, until refreshing is complete, the materialized view is in an uninitialized state, making it unavailable to the database server for query execution.



<a name="loiofaab95d872784a4c8d2a7bd3e74faa04__refresh_matview_standards1"/>

## Standards


<dl>
<dt><b>

ANSI/ISO SQL Standard

</b></dt>
<dd>

Not in the standard.



</dd>
</dl>



Suppose you create a materialized view, EmployeeConfid99, and then populate it with data using the following statements:

```
CREATE MATERIALIZED VIEW EmployeeConfid99 AS
   SELECT EmployeeID, Employees.DepartmentID, SocialSecurityNumber, Salary, ManagerID,
      Departments.DepartmentName, Departments.DepartmentHeadID
   FROM GROUPO.Employees, GROUPO.Departments
   WHERE Employees.DepartmentID=Departments.DepartmentID;
```

Later, you want to refresh the view and you want the view to be rebuilt. You could execute the following statement:

```
REFRESH MATERIALIZED VIEW EmployeeConfid99 FORCE BUILD;
```

> ### Caution:  
> When you are done with this example, drop the materialized view you created \(`DROP MATERIALIZED VIEW EmployeeConfid99`\). Otherwise, you cannot make schema changes to its underlying tables, Employees and Departments, when trying out other examples.

**Related Information**  


[CREATE MATERIALIZED VIEW Statement for Data Lake Relational Engine](create-materialized-view-statement-for-data-lake-relational-engine-d5c757e.md "Creates a materialized view.")

[ALTER MATERIALIZED VIEW Statement for Data Lake Relational Engine](alter-materialized-view-statement-for-data-lake-relational-engine-d958953.md "Alters a materialized view.")

[DROP Statement for Data Lake Relational Engine](drop-statement-for-data-lake-relational-engine-a61c216.md "Removes objects from the database.")

[REFRESH MATERIALIZED VIEW Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/817277ba6ce21014a14fa76ab2f0e6e1.html "Initializes or refreshes the data in a materialized view by executing its query definition.") :arrow_upper_right:

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[REVOKE Object-Level Privilege Statement for Data Lake Relational Engine](revoke-object-level-privilege-statement-for-data-lake-relational-engine-a3e7af2.md "Removes object-level privileges that were given using the GRANT statement.")

