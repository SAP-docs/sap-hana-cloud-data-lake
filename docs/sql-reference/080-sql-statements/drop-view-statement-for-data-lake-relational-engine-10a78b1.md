<!-- loio10a78b1d3ba748e8a3c096e90207a128 -->

# DROP VIEW Statement for Data Lake Relational Engine

Removes a view from the database.



<a name="loio10a78b1d3ba748e8a3c096e90207a128__section_azh_5fj_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
DROP VIEW [ IF EXISTS ] [ { <owner> | <schema-name> }.]<view-name>
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio10a78b1d3ba748e8a3c096e90207a128__drop_view_param1"/>

## Parameters


<dl>
<dt><b>

IF EXISTS

</b></dt>
<dd>

Use if you do not want an error returned when the DROP statement attempts to remove a database object that does not exist.



</dd>
</dl>



<a name="loio10a78b1d3ba748e8a3c096e90207a128__drop_view_remarks1"/>

## Remarks

DROP removes the definition of the indicated database structure.



<a name="loio10a78b1d3ba748e8a3c096e90207a128__drop_view_priv1"/>

## Privileges



### 

-   Requires one of:

    -   You own the view.
    -   DROP ANY VIEW system privilege
    -   DROP ANY OBJECT system privilege.
    -   DROP object-level privilege on the schema containing the view if the schema is owned by another user.


See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) or [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md) for assistance with granting privileges.



<a name="loio10a78b1d3ba748e8a3c096e90207a128__drop_view_sideffect1"/>

## Side Effects

-   Automatic commit. Clears the Data window in dbisql.



<a name="loio10a78b1d3ba748e8a3c096e90207a128__drop_view_standards1"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products – supported by SAP Adaptive Server Enterprise



<a name="loio10a78b1d3ba748e8a3c096e90207a128__drop_view_examples1"/>

## Examples

This example drops the view myview1 if it exits:

```
DROP IF EXISTS VIEW myview1;
```

**Related Information**  


[CREATE VIEW Statement for Data Lake Relational Engine](create-view-statement-for-data-lake-relational-engine-a61a051.md "Creates a view on the database. Views are used to give a different perspective on the data even though it is not stored that way.")

[ALTER VIEW Statement for Data Lake Relational Engine](alter-view-statement-for-data-lake-relational-engine-a613cd2.md "Replaces a view definition with a modified version.")

[DROP VIEW Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/3c389d94400946ca86449766a70a2877.html "Removes a view from the database.") :arrow_upper_right:

