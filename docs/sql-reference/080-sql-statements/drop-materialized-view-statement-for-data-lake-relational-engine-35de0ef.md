<!-- loio35de0ef70fde42bfb4c5c4b311cf8c69 -->

# DROP MATERIALIZED VIEW Statement for Data Lake Relational Engine

Removes a data type from the database.



<a name="loio35de0ef70fde42bfb4c5c4b311cf8c69__section_azh_5fj_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
DROP MATERIALIZED VIEW [ IF EXISTS ] [ { <owner> | <schema-name> }.]<mat-view-name>;
```



<a name="loio35de0ef70fde42bfb4c5c4b311cf8c69__drop_matview_param1"/>

## Parameters


<dl>
<dt><b>

IF EXISTS

</b></dt>
<dd>

Use if you do not want an error returned when the DROP statement attempts to remove a database object that does not exist.



</dd>
</dl>



<a name="loio35de0ef70fde42bfb4c5c4b311cf8c69__drop_matview_remarks1"/>

## Remarks

DROP removes the definition of the indicated database structure.

You cannot execute a DROP MATERIALIZED VIEW statement on an object that is currently being used by another connection.

Executing a DROP MATERIALIZED VIEW statement changes the status of all dependent regular views to INVALID. To determine view dependencies before dropping a materialized view, use the sa\_dependent\_views system procedure.



<a name="loio35de0ef70fde42bfb4c5c4b311cf8c69__drop_matview_priv1"/>

## Privileges



### 

Requires one of:

-   You own the materialized view.
-   DROP ANY MATERIALIZED VIEW system privilege
-   DROP ANY OBJECT system privilege.
-   DROP object-level privilege on the schema containing the materialized view if the schema is owned by another user.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) or [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md) for assistance with granting privileges.



<a name="loio35de0ef70fde42bfb4c5c4b311cf8c69__drop_matview_side_effects1"/>

## Side Effects

-   Automatic commit. Clears the Data window in dbisql.



<a name="loio35de0ef70fde42bfb4c5c4b311cf8c69__drop_matview_standards1"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products – supported by SAP Adaptive Server Enterprise



<a name="loio35de0ef70fde42bfb4c5c4b311cf8c69__drop_matview_examples1"/>

## Examples

This example drops the materialized view mymatview1 if it exists:

```
DROP IF EXISTS MATERIALIZD VIEW mymatview1;
```

**Related Information**  


[CREATE MATERIALIZED VIEW Statement for Data Lake Relational Engine](create-materialized-view-statement-for-data-lake-relational-engine-d5c757e.md "Creates a materialized view.")

[ALTER MATERIALIZED VIEW Statement for Data Lake Relational Engine](alter-materialized-view-statement-for-data-lake-relational-engine-d958953.md "Alters a materialized view.")

[sa\_dependent\_views System Procedure for Data Lake Relational Engine](../060-stored-procedures/sa-dependent-views-system-procedure-for-data-lake-relational-engine-3be5950.md "Returns the list of all dependent views for a given table or view.")

[DROP MATERIALIZED VIEW Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/50e76331a4664b5bb2c4454e80b5f8f4.html "Removes a data type from the database.") :arrow_upper_right:

