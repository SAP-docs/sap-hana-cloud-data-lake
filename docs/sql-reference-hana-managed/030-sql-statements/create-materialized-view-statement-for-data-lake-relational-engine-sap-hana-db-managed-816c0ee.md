<!-- loio816c0ee26ce21014b50bcd040d5dae25 -->

# CREATE MATERIALIZED VIEW Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Creates a materialized view.



## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:

-   Connected to SAP HANA database as a SAP HANA database user..



```
CREATE MATERIALIZED VIEW [ <schema-name>.]<view-name> [ ( <alt-column-names>) ]
   AS <select-statement> 
   [ { CHECK { AUTO | MANUAL } { FULL | INCREMENTAL } REFRESH 
     | { AUTO | MANUAL } FULL  REFRESH } ]
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio816c0ee26ce21014b50bcd040d5dae25__section_fyg_y3l_sqb"/>

## Parameters


<dl class="glossary">
<dt><b>

*<alt-column-names\>*

</b></dt>
<dd>

Specifies alternate names for the columns in the materialized view.

```
<alt-column-names> ::= ( <column-name>[, <column-name>...)
```

If you specify alternate columns names, the number of columns listed in *<alt-column-names\>* must match the number of columns in *<select-statement\>*. If you do not specify alternate column names, the names are set to those in *<select-statement\>*.



</dd><dt><b>

AS

</b></dt>
<dd>

Specifies, in the form of a SELECT statement, the data to use to populate the materialized view. A materialized view definition can only reference base tables; it cannot reference views, other materialized views, or temporary tables. *<select-statement\>* must contain column names or have an alias name specified. If you specify *<alt-column-names\>*, those names are used instead of the aliases specified in *<select-statement\>*.

Column names in the SELECT statement must be specified explicitly; you cannot use the SELECT \* construct. For example, you cannot specify CREATE MATERIALIZED VIEW matview AS SELECT \* FROM *<table-name\>*. Also, you should fully qualify objects names in the *<select-statement\>*.



</dd><dt><b>

CHECK

</b></dt>
<dd>

Validates the statement without actually creating the materialized view. When you specify the CHECK clause, data lake Relational Engine:

-   Performs the normal language checks that would be carried out if the clause was not specified. Any errors generated are returned. Since the view is not actually created, certain errors that could occur during creation \(for example, an error indicating that the specified view name already exists\) are not generated. This allows you to test any intended changes to the definition of the view, without a conflict with the naming of the view.
-   Verifies that the syntax is valid for an incremental view and returns any errors.

    Makes no changes to the view and no entry is recorded in the transaction log.


There is an implicit commit at the beginning of statement execution and a rollback at the end to release all locks obtained during execution.



</dd><dt><b>

AUTO | MANUAL

</b></dt>
<dd>

Specifies the refresh type of the materialized view. AUTO automatically refreshes the materialized view in a background transaction after it becomes stale due to modifications to the base tables it depends on. MANUAL requires execution of the REFRESH MATERIALIZE VIEW statement to refresh the contents of the materialized view.



</dd><dt><b>

FULL | INCREMENTAL

</b></dt>
<dd>

Specifies the refresh build method. FULL \(default\) truncates the materialized view and then populates the view by fully recomputing its content. INCREMENTAL attempts to refresh the materialized view using a delta computed since the last refresh. If an appropriate delta cannot be computed efficiently, then full refresh is performed. To perform an INCREMENTAL refresh on a materialized view, the view must:

1.  The materialized view must be uninitialized.
2.  If the materialized view does not contain outer joins, then the materialized view must have a unique HG index on non nullable columns.
3.  If the materialized view contains outer joins, then the materialized view must have a unique HG index on non nullable columns, or a unique HG index declared as WITH NULLS NOT DISTINCT on nullable columns.
4.  If the view definition is a grouped query, then the unique index columns must correspond to SELECT list items that are not aggregate functions. The view definition cannot contain:
    -   GROUPING SETS clauses
    -   CUBE clauses
    -   ROLLUP clauses
    -   DISTINCT clauses
    -   row limit clauses
    -   non-deterministic expressions
    -   self and recursive joins
    -   LATERAL, CROSS APPLY, or APPLY clauses

5.  The view definition must be a single select-project-join or grouped-select-project-join query block, and the grouped-select-project-join query block cannot contain a HAVING clause.
6.  The grouped-select-project-join query block must contain COUNT \( \* \) in the SELECT list, and is allowed only with the SUM and COUNT aggregate functions.
7.  An aggregate function in the SELECT list cannot be referenced in a complex expression. For example, SUM\( expression \) + 1 is not allowed in the SELECT list.
8.  If the SELECT list contains the SUM\(*<expression\>*\) aggregate function and *<expression\>* is a nullable expression, then the SELECT list must include a COUNT\(*<expression\>*\) aggregate function.
9.  If the view definition contains outer joins \(LEFT OUTER JOIN, RIGHT OUTER JOIN, FULL OUTER JOIN\), then the view definition must satisfy the following extra conditions:
    -   If a table, T, is referenced in an ON condition of an OUTER JOIN as a preserved side, then T must have a primary key and the primary key columns must be present in the SELECT list of the view. For example, the incremental materialized view V defined as SELECT T1.pk, R1.X FROM T1, T2 LEFT OUTER JOIN \( R1 KEY JOIN R2 \) ON T1.Y = R.Y has the preserved table, T1, referenced in the ON clause and its primary key column, T1.pk, is in the SELECT list of the incremental materialized view, V.
    -   For each NULL-supplying side of an outer join, there must be at least one base table such that one of its non-nullable columns is present in the SELECT list of the incremental materialized view. For example, for the incremental materialized view, V, defined as SELECT T1.pk, R1.X FROM T1, T2 LEFT OUTER JOIN \( R1 KEY JOIN R2 \) ON T1.Y = R1.Y, the NULL-supplying side of the left outer join is the table expression \( R1 KEY JOIN R2 \). The column R1.X is in the SELECT list of the V and R1.X is a non nullable column of the table R1.
    -   If the view is a grouped view and the previous condition does not hold, then for each NULL-supplying side of an outer join, there must be at least one base table, T, such that one of its non-nullable columns, T.C, is used in the aggregate function COUNT\( T.C \) in the SELECT list of the incremental materialized view. For example, for the incremental materialized view, V, defined as SELECT T1.pk, COUNT\( R1.X \) FROM T1, T2 LEFT OUTER JOIN \( R1 KEY JOIN R2 \) ON T1.Y = R1.Y GROUP BY T1.pk, the NULL-supplying side of the left outer join is the table expression \( R1 KEY JOIN R2 \). The aggregate function COUNT\( R1.X \) is in the SELECT list of the V and R1.X is a non-nullable column of the table R1.
    -   Any expression in the GROUP BY list must be present in the SELECT list.
    -   The following conditions must be satisfied by the predicates of the views with outer joins:
        -   The ON clause predicates for LEFT, RIGHT, and FULL OUTER JOINs must refer to both preserved and NULL-supplying table expression. For example, T LEFT OUTER JOIN R ON R.X = 1 does not satisfy this condition as the predicate R.X=1 references only the NULL-supplying side R.
        -   Any predicate must reject NULL-supplied rows produced by a nested outer join. In other words, if a predicate refers to a table expression which is NULL-supplied by a nested outer join, then it must reject all rows which have nulls generated by that outer join.

            For example, the view V1 SELECT T1.pk, R1.X FROM T1, T2 LEFT OUTER JOIN \( R1 KEY JOIN R2 \) ON \( T1.Y = R1.Y \) WHERE R1.Z = 10 has the predicate R1.Z=10 referencing the table R1 which can be NULL-supplied by the T2 LEFT OUTER JOIN \( R1 KEY JOIN R2 \), hence it must reject any NULL-supplied rows. This is true because the predicate evaluates to UNKNOWN when the column R1.Z is NULL.

            However, the view V2 SELECT T1.pk, R1.X FROM T1, T2 LEFT OUTER JOIN \( R1 KEY JOIN R2 \) ON \( T1.Y = R1.Y \) WHERE R1.Z IS NULL does not have this property. The predicate R1.Z IS NULL references the NULL-supplying side R1 but it evaluates to TRUE when the table R1 is NULL-supplied \(that is, the R1.Z column is null\). The method of rejecting NULL-supplied rows is not as restrictive as a NULL-intolerant property. For example, the predicate R.X IS NOT DISTINCT FROM T.X and rowid\( T \) IS NOT NULL is not NULL-intolerant on the table T as it evaluates to TRUE when T.X is NULL. However, the predicate rejects all the rows which are NULL-supplied on the base table T.






</dd>
</dl>



<a name="loio816c0ee26ce21014b50bcd040d5dae25__section_lht_1jl_sqb"/>

## Remarks

When you create a materialized view, if a refresh type is not specified, it is MANUAL.A new materialized view is uninitialized. That is, it has not been manually refreshed \(populated with data\) at least once. To initialize the view, execute a REFRESH MATERIALIZED VIEW statement.

For an AUTO materialized view, automatic refreshes do not begin until after the materialized view is initialized.

Several database and server options must be in effect to create a materialized view. See *Materialized Views Restrictions*.



<a name="loio816c0ee26ce21014b50bcd040d5dae25__section_cmj_vpr_wwb"/>

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



<a name="loio816c0ee26ce21014b50bcd040d5dae25__section_yzk_cjl_sqb"/>

## Side Effects

Automatic commit. While executing, the CREATE MATERIALIZED VIEW statement places exclusive locks, without blocking, on all tables referenced by the materialized view. If one of the referenced tables cannot be locked, the statement fails and an error is returned.



<a name="loio816c0ee26ce21014b50bcd040d5dae25__section_yst_fjl_sqb"/>

## Standards


<dl>
<dt><b>

ANSI/ISO SQL Standard

</b></dt>
<dd>

Not in the standard.



</dd>
</dl>



## Example

This example creates materialized view V\_BAR1, which is configured to automatically refresh when staleness is detected.

```
CREATE MATERIALIZED VIEW V_BAR1 AS SELECT C1, C2, C3 FROM BAR AUTO FULL REFRESH;
```

This example validates the syntax to create materialized view V\_BAR2. The syntax is deemed valid and no error is returned, but V\_BAR2 is not actually created.

```
CREATE MATERIALIZED VIEW V_BAR2 AS SELECT DISTINCT C1, C2, C3 FROM BAR CHECK AUTO FULL REFRESH;
```

This example validates the syntax to create materialized view V\_BAR3. It returns the error "definition contains an illegal construct: 'elimination of duplicates'" because a view configured for INCREMENTAL refresh does not support DISTINCT in its definition.

```
CREATE MATERIALIZED VIEW V_BAR3 AS SELECT DISTINCT C1, C2, C3 FROM BAR CHECK AUTO INCREMENTAL REFRESH;
```

**Related Information**  


[ALTER MATERIALIZED VIEW Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](alter-materialized-view-statement-for-data-lake-relational-engine-sap-hana-db-managed-8169459.md "Alters a materialized view.")

[DROP MATERIALIZED VIEW Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](drop-materialized-view-statement-for-data-lake-relational-engine-sap-hana-db-managed-50e7633.md "Removes a data type from the database.")

[Materialized Views Restrictions in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2024_3_QRC/en-US/819dad776ce21014a540de412c46da06.html "There are some requirements and restrictions that must be met when creating, initializing, refreshing, and using materialized views.") :arrow_upper_right:

[Refresh and Build Types for Materialized Views in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2024_3_QRC/en-US/30ca3ca6ffbc4e6e804959f02571e62c.html "You can control when (refresh type): MANUAL or AUTO and how (build type): FULL or INCREMENTAL a materialized view is refreshed.") :arrow_upper_right:

[CREATE MATERIALIZED VIEW Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/d5c757e1c0dd4fdb85bde37bad9b8bb3.html "Creates a materialized view.") :arrow_upper_right:

