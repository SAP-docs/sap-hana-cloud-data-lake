<!-- loio817277ba6ce21014a14fa76ab2f0e6e1 -->

# REFRESH MATERIALIZED VIEW Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Initializes or refreshes the data in a materialized view by executing its query definition.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Executing SQL Statements](remote-execute-usage-examples-for-executing-sql-statements-fd99ac0.md).



```
REFRESH MATERIALIZED VIEW [ [/pandoc/div/div/horizontalrule/codeblock/span/span
     {""}) [/pandoc/div/div/horizontalrule/codeblock/span/span/varname
     {"varname"}) <schema-name> (varname] (span].][/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <mat_view_name> (varname]
   [ FORCE BUILD ]
```



<a name="loio817277ba6ce21014a14fa76ab2f0e6e1__section_itj_mqw_brb"/>

## Parameters

 FORCE BUILD
 :   By default, when you execute a REFRESH MATERIALIZED VIEW statement, the database server checks whether the materialized view is stale \(that is, underlying tables have changed since the materialized view was last refreshed\). If it is not stale, the refresh does not take place. Specify the FORCE BUILD clause to force a refresh of the materialized view regardless of whether the materialized view is stale.

 

<a name="loio817277ba6ce21014a14fa76ab2f0e6e1__section_lrx_mqw_brb"/>

## Remarks

Use this statement to initialize or refresh the materialized view.

If a REFRESH MATERIALIZED VIEW statement is executed against a materialized view that is not stale, a refresh is not performed unless the FORCE BUILD clause is specified.

This statement cannot be executed when the connection has cursors opened with the WITH HOLD clause that use either statement or transaction snapshots.



<a name="loio817277ba6ce21014a14fa76ab2f0e6e1__section_vtd_ffy_wwb"/>

## Privileges



### 

You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loio817277ba6ce21014a14fa76ab2f0e6e1__section_hsm_pqw_brb"/>

## Side Effects

A refresh of a materialized view fails if there is an open cursor because the exclusive locks cannot be acquired.

A checkpoint is performed at the beginning of execution.

Automatic commits are performed at the beginning and end of execution.

While executing, an exclusive schema lock is placed on the materialized view being refreshed using the connection blocking option, and shared schema locks, without blocking, are placed on all tables referenced by the materialized view. Also, until refreshing is complete, the materialized view is in an uninitialized state, making it unavailable to the database server for query execution.



<a name="loio817277ba6ce21014a14fa76ab2f0e6e1__section_tcc_qqw_brb"/>

## Standards

 ANSI/ISO SQL Standard
 :   Not in the standard.

 

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


[ALTER MATERIALIZED VIEW Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](alter-materialized-view-statement-for-data-lake-relational-engine-sap-hana-db-managed-8169459.md "Alters a materialized view.")

[CREATE MATERIALIZED VIEW Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](create-materialized-view-statement-for-data-lake-relational-engine-sap-hana-db-managed-816c0ee.md "Creates a materialized view.")

[REFRESH MATERIALIZED VIEW Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/faab95d872784a4c8d2a7bd3e74faa04.html "Initializes or refreshes the data in a materialized view by executing its query definition.") :arrow_upper_right:

[DROP Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](drop-statement-for-data-lake-relational-engine-sap-hana-db-managed-367d71d.md "Removes objects from the database.")
