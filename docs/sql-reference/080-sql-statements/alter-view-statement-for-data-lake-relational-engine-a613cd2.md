<!-- loioa613cd2484f2101580a1c565befd8049 -->

# ALTER VIEW Statement for Data Lake Relational Engine 

Replaces a view definition with a modified version.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.





### Syntax 1 – Alter the Structure of the View

```
ALTER VIEW
   ...[ [/pandoc/div/div/horizontalrule/horizontalrule/codeblock/span/span
     {""}) { [/pandoc/div/div/horizontalrule/horizontalrule/codeblock/span/span/varname
     {"varname"}) <owner> (varname] | [/pandoc/div/div/horizontalrule/horizontalrule/codeblock/span/span/varname
     {"varname"}) <schema-name> (varname] } (span].][/pandoc/div/div/horizontalrule/horizontalrule/codeblock/span/varname
     {"varname"}) <view-name> (varname] [ ( [/pandoc/div/div/horizontalrule/horizontalrule/codeblock/span/varname
     {"varname"}) <column-name> (varname] [ , … ] ) ]
   ...AS [/pandoc/div/div/horizontalrule/horizontalrule/codeblock/span/varname
     {"varname"}) <select-statement> (varname]
   ...[ WITH CHECK OPTION ]
```



### Syntax 2 – Change Attributes for the View

```
ALTER VIEW
   ...[ [/pandoc/div/div/horizontalrule/horizontalrule/codeblock/span/span
     {""}) { [/pandoc/div/div/horizontalrule/horizontalrule/codeblock/span/span/varname
     {"varname"}) <owner> (varname] | [/pandoc/div/div/horizontalrule/horizontalrule/codeblock/span/span/varname
     {"varname"}) <schema-name> (varname] } (span].][/pandoc/div/div/horizontalrule/horizontalrule/codeblock/span/varname
     {"varname"}) <view-name> (varname] 
   ...{ SET HIDDEN | RECOMPILE | DISABLE | ENABLE }
```



<a name="loioa613cd2484f2101580a1c565befd8049__alter_view_parameters1"/>

## Parameters

 AS *<select-statement\>*
 :   The SELECT statement on which the view is based must not contain an ORDER BY clause, a subquery in the SELECT list, or a TOP or FIRST qualification. It may have a GROUP BY clause and may be a UNION.

  WITH CHECK OPTION
 :   Rejects any updates and inserts to the view that do not meet the criteria of the views as defined by its SELECT statement. However, data lake Relational Engine currently ignores this option \(it supports the syntax for compatibility reasons\).

  SET HIDDEN
 :   Obfuscates the definition of the view and cause the view to become hidden from view. Explicit references to the view still work.

    > ### Caution:  
    > The SET HIDDEN operation is irreversible.

    When you use SET HIDDEN, you can unload and reload the view into other databases. Debugging using the debugger does not show the view definition, nor is it available through procedure profiling. If you need to change the definition of a hidden view, you must drop the view and create it again using the `CREATE VIEW` statement.

  RECOMPILE
 :   Re-creates the column definitions for the view. Identical in functionality to the ENABLE clause, except you can use it on a view that is not disabled.

  DISABLE
 :   Disables the view from use by the database server.

    When you use the DISABLE clause, the view is no longer available for use by the database server to answer queries. Disabling a view is similar to dropping one, except that the view definition remains in the database. Disabling a view also disables any dependent views. Therefore, the DISABLE clause requires exclusive access, not only to the view being disabled, but to any dependent views, which are also disabled.

  ENABLE
 :   Enables a disabled view, which causes the database server to re-create the column definitions for the view. Before you enable a view, you must enable any views on which it depends.

 

<a name="loioa613cd2484f2101580a1c565befd8049__alter_view_remarks1"/>

## Remarks

When you alter a view, existing permissions on the view are maintained and do not require reassignment. Instead of using the `ALTER VIEW` statement, you could also drop the view and re-create it using `DROP VIEW` and `CREATE VIEW`, respectively. If you do this, view permissions must be reassigned.

After completing the view alteration using Syntax 1, the database server recompiles the view. Depending on the type of change you made, if there are dependent views, the database server attempts to recompile them. If you made changes that impact a dependent view, that view may become invalid, requiring you to alter the definition for the dependent view.

> ### Caution:  
> If the `SELECT` statement defining the view contains an asterisk \(\*\), the number of the columns in the view could change if columns were added or deleted from the underlying tables. The names and data types of the view columns could also change.

Altering the structure of a view requires that you replace the entire view definition with a new definition, much as you would when creating the view using the `CREATE VIEW` statement.



<a name="loioa613cd2484f2101580a1c565befd8049__alter_view_privilege1"/>

## Privileges



### 

The privilege required varies by clause. 


<table>
<tr>
<th valign="top">

Clause



</th>
<th valign="top">

Privilege Required



</th>
</tr>
<tr>
<td valign="top">

Alter the SELECT clause of the view



</td>
<td valign="top">

Requires one of:

-   You own the view and its underlying objects.
-   ALTER ANY VIEW system privilege.
-   ALTER ANY OBJECT system privilege.
-   ALTER object-level privilege on the schema containing the view if the schema is owned by another user.

If you don't own the underlying objects referenced by the view, then you also need one of:

-   SELECT object-level privilege on the underlying objects.
-   SELECT ANY TABLE system privilege.
-   SELECT object-level privilege on the schema containing the objects if the schema is owned by another user.



</td>
</tr>
<tr>
<td valign="top">

ENABLE clause



</td>
<td valign="top">

No privilege required.



</td>
</tr>
<tr>
<td valign="top">

DISABLE clause or SET HIDDEN clause



</td>
<td valign="top">

Requires one of:

-   You own the view.
-   ALTER ANY VIEW system privilege.
-   ALTER ANY OBJECT system privilege.
-   ALTER object-level privilege on the schema containing the view if the schema is owned by another user.



</td>
</tr>
<tr>
<td valign="top">

RECOMPILE clause



</td>
<td valign="top">

Requires one of:

-   You own the view and its underlying objects.
-   ALTER ANY VIEW system privilege.
-   ALTER ANY OBJECT system privilege.

If you don't own the underlying objects of the view, then you also need one of:

-   SELECT object-level privilege on the underlying objects.
-   SELECT ANY TABLE system privilege.
-   SELECT object-level privilege on the schema containing the objects if the schema is owned by another user.



</td>
</tr>
</table>

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) or [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md) for assistance with granting privileges. 



<a name="loioa613cd2484f2101580a1c565befd8049__alter_view_sideefects1"/>

## Side Effects

-   Automatic commit
-   All procedures and triggers are unloaded from memory, so that any procedure or trigger that references the view reflects the new view definition. The unloading and loading of procedures and triggers can have a performance impact if you regularly alter views.



<a name="loioa613cd2484f2101580a1c565befd8049__alter_view_standards1"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise

**Related Information**  


[CREATE TRIGGER Statement for Data Lake Relational Engine](create-trigger-statement-for-data-lake-relational-engine-3be4860.md "Creates a trigger on a table. This statement applies to data lake Relational Engine catalog store tables only.")

[DROP TRIGGER Statement for Data Lake Relational Engine](drop-trigger-statement-for-data-lake-relational-engine-3be4974.md "Removes a trigger from the database. This statement applies to data lake Relational Engine catalog store tables only.")

[DISCONNECT Statement \[Interactive SQL\] for Data Lake Relational Engine](disconnect-statement-interactive-sql-for-data-lake-relational-engine-a61bf2a.md "Drops a connection with the database.")

[Identifying and Fixing Invalid Dependent Views for Data Lake Relational Engine](identifying-and-fixing-invalid-dependent-views-for-data-lake-relational-engine-a38963a.md "Check for, and correct, any dependent views that become invalid because of changes to their underlying tables.")

[ALTER VIEW Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/6ef54831fa96405b83c2a82cf9a88b9a.html "Replaces a view definition with a modified version.") :arrow_upper_right:

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[REVOKE Object-Level Privilege Statement for Data Lake Relational Engine](revoke-object-level-privilege-statement-for-data-lake-relational-engine-a3e7af2.md "Removes object-level privileges that were given using the GRANT statement.")

