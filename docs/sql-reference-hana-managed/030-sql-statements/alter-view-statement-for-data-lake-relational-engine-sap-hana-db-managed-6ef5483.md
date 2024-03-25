<!-- loio6ef54831fa96405b83c2a82cf9a88b9a -->

# ALTER VIEW Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Replaces a view definition with a modified version.



## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:

-   Connected to SAP HANA database as a SAP HANA database user..





### Syntax 1 – Alter the Structure of the View

```
ALTER VIEW
   ...[ <schema-name>.]<view-name> [ ( <column-name> [ , … ] ) ]
   ...AS <select-statement>
   ...[ WITH CHECK OPTION ]
```



### Syntax 2 – Change Attributes for the View

```
ALTER VIEW
   ...[ <schema-name>.]<view-name> 
   ...{ SET HIDDEN | RECOMPILE | DISABLE | ENABLE }
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio6ef54831fa96405b83c2a82cf9a88b9a__section_d1t_j1l_sqb"/>

## Parameters


<dl>
<dt><b>

AS *<select-statement\>*

</b></dt>
<dd>

The SELECT statement on which the view is based must not contain an ORDER BY clause, a subquery in the SELECT list, or a TOP or FIRST qualification. It may have a GROUP BY clause and may be a UNION.



</dd><dt><b>

WITH CHECK OPTION

</b></dt>
<dd>

Rejects any updates and inserts to the view that do not meet the criteria of the views as defined by its SELECT statement. However, data lake Relational Engine currently ignores this option \(it supports the syntax for compatibility reasons\).



</dd><dt><b>

SET HIDDEN

</b></dt>
<dd>

Obfuscates the definition of the view and cause the view to become hidden from view. Explicit references to the view still work.

> ### Caution:  
> The SET HIDDEN operation is irreversible.

When you use SET HIDDEN, you can unload and reload the view into other databases. Debugging using the debugger does not show the view definition, nor is it available through procedure profiling. If you need to change the definition of a hidden view, you must drop the view and create it again using the `CREATE VIEW` statement.



</dd><dt><b>

RECOMPILE

</b></dt>
<dd>

Re-creates the column definitions for the view. Identical in functionality to the ENABLE clause, except you can use it on a view that is not disabled.



</dd><dt><b>

DISABLE

</b></dt>
<dd>

Disables the view from use by the database server.

When you use the DISABLE clause, the view is no longer available for use by the database server to answer queries. Disabling a view is similar to dropping one, except that the view definition remains in the database. Disabling a view also disables any dependent views. Therefore, the DISABLE clause requires exclusive access, not only to the view being disabled, but to any dependent views, which are also disabled.



</dd><dt><b>

ENABLE

</b></dt>
<dd>

Enables a disabled view, which causes the database server to re-create the column definitions for the view. Before you enable a view, you must enable any views on which it depends.



</dd>
</dl>



<a name="loio6ef54831fa96405b83c2a82cf9a88b9a__section_mjp_l1l_sqb"/>

## Remarks

When you alter a view, existing permissions on the view are maintained and do not require reassignment. Instead of using the `ALTER VIEW` statement, you could also drop the view and re-create it using `DROP VIEW` and `CREATE VIEW`, respectively. If you do this, view permissions must be reassigned.

After completing the view alteration using Syntax 1, the database server recompiles the view. Depending on the type of change you made, if there are dependent views, the database server attempts to recompile them. If you made changes that impact a dependent view, that view may become invalid, requiring you to alter the definition for the dependent view.

> ### Caution:  
> If the `SELECT` statement defining the view contains an asterisk \(\*\), the number of the columns in the view could change if columns were added or deleted from the underlying tables. The names and data types of the view columns could also change.

Altering the structure of a view requires that you replace the entire view definition with a new definition, much as you would when creating the view using the `CREATE VIEW` statement.



<a name="loio6ef54831fa96405b83c2a82cf9a88b9a__section_vkp_f3q_wwb"/>

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




</dd>
</dl>



<a name="loio6ef54831fa96405b83c2a82cf9a88b9a__section_m1j_n1l_sqb"/>

## Side Effects

-   Automatic commit
-   All procedures and triggers are unloaded from memory, so that any procedure or trigger that references the view reflects the new view definition. The unloading and loading of procedures and triggers can have a performance impact if you regularly alter views.



<a name="loio6ef54831fa96405b83c2a82cf9a88b9a__section_bn4_41l_sqb"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loio6ef54831fa96405b83c2a82cf9a88b9a__section_cnj_5zh_pkb"/>

## Examples

Assuming you have a virtual table SYSHDL\_CONTAINER1.V\_VIEWS\_T1 that returns COL\_A only. This statement changes the SELECT statement of the data lake Relational Engine view named VIEW\_T1 tp return COL\_A AND COL\_B.

```
CALL SYSHDL_CONTAINER1.REMOTE_EXECUTE ('ALTER VIEW VIEW_T1 AS SELECT COL_A, COL_B FROM T1');
```

This statement refreshes the SAP HANA database virtual table SYSHDL\_CONTAINER1.V\_VIEW\_T1 that points to the data lake Relational Engine view named VIEW\_T1.

```
ALTER VIRTUAL TABLE SYSHDL_CONTAINER1.V_VIEW_T1 REFRESH DEFINITION;
```

**Related Information**  


[CREATE VIEW Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](create-view-statement-for-data-lake-relational-engine-sap-hana-db-managed-4d41128.md "Creates a view on the database. Views are used to give a different perspective on the data even though it is not stored that way.")

[DROP VIEW Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](drop-view-statement-for-data-lake-relational-engine-sap-hana-db-managed-3c389d9.md "Removes a view from the database.")

[ALTER VIEW Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/a613cd2484f2101580a1c565befd8049.html "Replaces a view definition with a modified version.") :arrow_upper_right:

