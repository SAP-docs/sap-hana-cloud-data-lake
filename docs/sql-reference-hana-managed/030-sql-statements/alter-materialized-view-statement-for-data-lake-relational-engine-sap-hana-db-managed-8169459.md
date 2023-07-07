<!-- loio816945966ce210149a80b8603addbc83 -->

# ALTER MATERIALIZED VIEW Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Alters a materialized view.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Executing SQL Statements](remote-execute-usage-examples-for-executing-sql-statements-fd99ac0.md).



```
ALTER MATERIALIZED VIEW [ <schema-name>.]<mat-view-name> 
   { { ENABLE | DISABLE }
   | SET HIDDEN
   | RENAME { PARTITION | SUBPARTITION } <range-partition-name> TO <new-range-partition-name>
   | SPLIT { PARTITION | SUBPARTITION } <split-object>
   | MERGE { PARTITION | SUBPARTITION } <partition-name-1> INTO <partition-name-2> 
   | PARTITION BY { <range-partitioning-scheme>  
                  | <hash-partitioning-scheme> 
                  | <hash-range-partitioning-scheme> }
   | SUBPARTITION BY RANGE <range-partition-decl>
   | ADD { PARTITION | SUBPARTITION } BY RANGE <range-partition-decl>
   | UNPARTITION
   | [ { AUTO | MANUAL } { FULL | INCREMENTAL } REFRESH ] }
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio816945966ce210149a80b8603addbc83__section_sky_qtk_sqb"/>

## Parameters


<dl class="glossary">
<dt><b>

SET HIDDEN

</b></dt>
<dd>

Use the SET HIDDEN clause to obfuscate the definition of a materialized view. *This setting is irreversible*.



</dd><dt><b>

\{ ENABLE | DISABLE \}

</b></dt>
<dd>

Use the ENABLE clause to enable a disabled materialized view, making it available for the database server to use. This clause has no effect on a view that is already enabled. After using this clause, you must refresh the view to initialize it, and recreate any text indexes that were dropped when the view was disabled.

Use the DISABLE clause to disable use of the view by the database server. When you disable a materialized view, the database server drops the data and indexes for the view.



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

1.  Satisfy the following criteria:
    -   The view must be uninitialized.
    -   If the view does not contain outer joins, then the view must have a unique index on non nullable columns. If the view contains outer joins, then the view must have a unique index on non nullable columns, or a unique index declared as WITH NULLS NOT DISTINCT on nullable columns.
    -   If the view definition is a grouped query, then the unique index columns must correspond to SELECT list items that are not aggregate functions. The view definition cannot contain:
        -   GROUPING SETS clauses
        -   CUBE clauses
        -   ROLLUP clauses
        -   DISTINCT clauses
        -   row limit clauses
        -   non-deterministic expressions
        -   self and recursive joins
        -   LATERAL, CROSS APPLY, or APPLY clauses

    -   The view definition must be a single select-project-join or grouped-select-project-join query block, and the grouped-select-project-join query block cannot contain a HAVING clause.
    -   The grouped-select-project-join query block must contain COUNT \( \* \) in the SELECT list, and is allowed only with the SUM and COUNT aggregate functions.
    -   An aggregate function in the SELECT list cannot be referenced in a complex expression. For example, SUM\( expression \) + 1 is not allowed in the SELECT list.
    -   If the SELECT list contains the SUM\(*<expression\>*\) aggregate function and *<expression\>* is a nullable expression, then the SELECT list must include a COUNT\(*<expression\>*\) aggregate function.
    -   If the view definition contains outer joins \(LEFT OUTER JOIN, RIGHT OUTER JOIN, FULL OUTER JOIN\), then the view definition must satisfy the following extra conditions:
        1.  If a table, T, is referenced in an ON condition of an OUTER JOIN as a preserved side, then T must have a primary key and the primary key columns must be present in the SELECT list of the view. For example, the incremental materialized view V defined as SELECT T1.pk, R1.X FROM T1, T2 LEFT OUTER JOIN \( R1 KEY JOIN R2 \) ON T1.Y = R.Y has the preserved table, T1, referenced in the ON clause and its primary key column, T1.pk, is in the SELECT list of the incremental materialized view, V.
        2.  For each NULL-supplying side of an outer join, there must be at least one base table such that one of its non-nullable columns is present in the SELECT list of the incremental materialized view. For example, for the incremental materialized view, V, defined as SELECT T1.pk, R1.X FROM T1, T2 LEFT OUTER JOIN \( R1 KEY JOIN R2 \) ON T1.Y = R1.Y, the NULL-supplying side of the left outer join is the table expression \( R1 KEY JOIN R2 \). The column R1.X is in the SELECT list of the V and R1.X is a non nullable column of the table R1.
        3.  If the view is a grouped view and the previous condition does not hold, then for each NULL-supplying side of an outer join, there must be at least one base table, T, such that one of its non-nullable columns, T.C, is used in the aggregate function COUNT\( T.C \) in the SELECT list of the incremental materialized view. For example, for the incremental materialized view, V, defined as SELECT T1.pk, COUNT\( R1.X \) FROM T1, T2 LEFT OUTER JOIN \( R1 KEY JOIN R2 \) ON T1.Y = R1.Y GROUP BY T1.pk, the NULL-supplying side of the left outer join is the table expression \( R1 KEY JOIN R2 \). The aggregate function COUNT\( R1.X \) is in the SELECT list of the V and R1.X is a non-nullable column of the table R1.
        4.  The following conditions must be satisfied by the predicates of the views with outer joins:
            -   The ON clause predicates for LEFT, RIGHT, and FULL OUTER JOINs must refer to both preserved and NULL-supplying table expression. For example, T LEFT OUTER JOIN R ON R.X = 1 does not satisfy this condition as the predicate R.X=1 references only the NULL-supplying side R.
            -   Any predicate must reject NULL-supplied rows produced by a nested outer join. In other words, if a predicate refers to a table expression which is NULL-supplied by a nested outer join, then it must reject all rows which have nulls generated by that outer join.

                For example, the view V1 SELECT T1.pk, R1.X FROM T1, T2 LEFT OUTER JOIN \( R1 KEY JOIN R2 \) ON \( T1.Y = R1.Y \) WHERE R1.Z = 10 has the predicate R1.Z=10 referencing the table R1 which can be NULL-supplied by the T2 LEFT OUTER JOIN \( R1 KEY JOIN R2 \), hence it must reject any NULL-supplied rows. This is true because the predicate evaluates to UNKNOWN when the column R1.Z is NULL.

                However, the view V2 SELECT T1.pk, R1.X FROM T1, T2 LEFT OUTER JOIN \( R1 KEY JOIN R2 \) ON \( T1.Y = R1.Y \) WHERE R1.Z IS NULL does not have this property. The predicate R1.Z IS NULL references the NULL-supplying side R1 but it evaluates to TRUE when the table R1 is NULL-supplied \(that is, the R1.Z column is null\). The method of rejecting NULL-supplied rows is not as restrictive as a NULL-intolerant property. For example, the predicate R.X IS NOT DISTINCT FROM T.X and rowid\( T \) IS NOT NULL is not NULL-intolerant on the table T as it evaluates to TRUE when T.X is NULL. However, the predicate rejects all the rows which are NULL-supplied on the base table T.


        5.  A unique HG index defined for the materialized view must exist. If the materialized view contains outer joins, then the materialized view must have a unique HG index on non nullable columns or a unique HG index with at least one column non-nullable. If the materialized view does not contain outer joins, then the materialized view must have a unique index on non nullable columns.
        6.  Any expression in the GROUP BY list must be present in the SELECT list.


2.  Have a unique HG index defined for the materialized view.
    -   If the materialized view does not contain outer joins, then the materialized view must have a unique index on non nullable columns.
    -   If the materialized view does contain outer joins, then the materialized view must have a unique HG index on non nullable columns or a unique HG index with at least one column non-nullable.




</dd><dt><b>

SPLIT \{ PARTITION | SUBPARTITION \} *<split-object\>*

</b></dt>
<dd>

Splits an existing range partition or subpartition.

```
<split-object> ::= <range-partition-decl> 
        INTO ( <range-partition-decl>, <range-partition-decl> )
```

When splitting a partition or subpartition, the names of the new partitions must be unique and cannot include the name of the original partition. All data from the original partition must fit into only one of the resulting partitions. Data cannot move between partitions.

When splitting a partition or subpartition, the upper boundary of the new partitions must be equal to the upper boundary of the original partition. For example, if P1 has a boundary of 100 and you split P1 into P1A and P1B, the boundary of P1B must be 100.



</dd><dt><b>

MERGE \{ PARTITION | SUBPARTITION \}

</b></dt>
<dd>

Merges *<partition-name-1\>* into *<partition-name-2\>*. Two partitions can be merged if they are adjacent partitions. You can only merge a partition with a lower partition value into the adjacent partition with a higher partition value. Note that the server does not check CREATE privilege into which the partition is merged. For an example of how to create adjacent partitions, see CREATE TABLE Statement examples.



</dd><dt><b>

PARTITION BY

</b></dt>
<dd>

Divides large tables into smaller, more manageable storage objects. Partitions share the same logical attributes of the parent table, but can be placed in separate dbspaces and managed individually. Data lake Relational Engine supports several table partitioning schemes:

-   Hash-partitions
-   Range-partitions
-   Hash range-partitions

A partition-key is the column or columns that contain the table partitioning keys. Partition keys can contain NULL and DEFAULT values, but cannot contain:

-   LOB \(BLOB or CLOB\) columns
-   BINARY, or VARBINARY columns
-   CHAR or VARCHAR columns whose length is over 255 bytes
-   BIT columns
-   FLOAT/DOUBLE/REAL columns



</dd>
<dd>

Restrictions when partitioning an existing materialized view:

-   For range partitioning, any existing data in the table must exist within the upper bound of the first partition of the materialized view or the materialized view must be uninitialized.
-   For hash partitioning and range subpartitioning of a hash table, the table must be empty or the materialized view must be uninitialized.

Use the TRUNCATE MATERIALIZED VIEW to uninitialize an initialized materialized view.



</dd>
<dd>


<dl>
<dt><b>

*<range-partitioning-scheme\>*

</b></dt>
<dd>

Partitions rows by a range of values in the partitioning column. Range partitioning is restricted to a single partition key column and a maximum of 1024 partitions. In a range-partitioning-scheme, the partition-key is the column that contains the table partitioning keys:

```
<range-partitioning-scheme> ::=
   RANGE ( <column-name> ) ( <range-partition-decl> [,...] )
```


<dl>
<dt><b>

*<range-partition-decl\>*

</b></dt>
<dd>

```
<range-partition-decl> ::=
   <partition-name> VALUES <= ( { <constant-expression> | MAX } [,...] )
```


<dl>
<dt><b>

*<partition-name\>*

</b></dt>
<dd>

Specifies the name of a new partition on which table rows are stored. Partition names must be unique within the set of partitions on a table.



</dd><dt><b>

*<VALUES\>*

</b></dt>
<dd>

Specifies the inclusive upper bound for each partition \(in ascending order\). The user must specify the partitioning criteria for each range partition to guarantee that each row is distributed to only one partition. NULLs are allowed for the partition column and rows with NULL as partition key value belong to the first table partition. However, NULL cannot be the bound value.

There is no lower bound \(MIN value\) for the first partition. Rows of NULL cells in the first column of the partition key will go to the first partition. For the last partition, you can either specify an inclusive upper bound or MAX. If the upper bound value for the last partition is not MAX, loading or inserting any row with partition key value larger than the upper bound value of the last partition generates an error.



</dd><dt><b>

MAX

</b></dt>
<dd>

Denotes the infinite upper bound and can only be specified for the last partition.



</dd>
</dl>



</dd>
</dl>

Restrictions:

-   Partition bounds must be constants, not constant expressions.

-   Partition bounds must be in ascending order according to the order in which the partitions were created. That is, the upper bound for the second partition must be higher than for the first partition, and so on. In addition, partition bound values must be compatible with the corresponding partition-key column data type.

-   If a bound value has a different data type than that of its corresponding partition key column, data lake Relational Engine converts the bound value to the data type of the partition key column, with these exceptions:

    -   Explicit conversions are not allowed. This example attempts an explicit conversion from INT to VARCHAR and generates an error:

        ```
        CREATE TABLE EMPLOYEES(EMP_NAME VARCHAR(20)) PARTITION BY RANGE(EMP_NAME)
           (P1 VALUES <= (CAST (1 AS VARCHAR(20))), P2 VALUES <= (CAST (10 AS VARCHAR(20)));
        ```

    -   Implicit conversions that result in data loss are not allowed. In this example, the partition bounds are not compatible with the partition key type. Rounding assumptions may lead to data loss and an error is generated:

        ```
        CREATE TABLE EMP_ID (ID INT) PARTITION BY RANGE(ID) (P1 VALUES <= (10.5), P2 VALUES <= (100.5));
        ```

        In this example, the partition bounds and the partition key data type are compatible. The bound values are directly converted to float values. No rounding is required, and conversion is supported:

        ```
        CREATE TABLE ID_EMP (ID FLOAT) PARTITION BY RANGE(ID) (P1 VALUES <= (10), P2 VALUES <= (100));
        ```


-   Conversions from non-binary data types to binary data types are not allowed. For example, this conversion is not allowed and returns an error:

    ```
    CREATE TABLE NEWEMP (NAME BINARY) PARTITION BY RANGE(name) 
       (P1 VALUES <= ('Maarten'), P2 VALUES <= ('Zymmerman');
    ```

-   NULL cannot be used as a boundary in a range-partitioned table.
-   The row will be in the first partition if the cell value of the 1st column of the partition key evaluated to be NULL. Data lake Relational Engine supports only single column partition keys, so any NULL in the partition key distributes the row to the first partition.



</dd><dt><b>

*<hash-partitioning-scheme\>*

</b></dt>
<dd>

Maps data to partitions based on partition-key values processed by an internal hashing function. Hash partition keys are restricted to a maximum of eight columns with a combined declared column width of 5300 bytes or less. For hash partitions, the table creator determines only the partition key columns; the number and location of the partitions are determined internally.

```
<hash-partitioning-scheme> ::=
   HASH ( <column-name> [,... ] )
```

Restrictions:

-   You cannot add, drop, merge, or split a hash partition.
-   You cannot add or drop a column from a hash partition key.



</dd><dt><b>

*<hash-range-partitioning-scheme\>*

</b></dt>
<dd>

Maps data to partitions based on partition-key values processed by an internal hashing function and subpartitions the hash-partitioned table by range.

```
<hash-range-partitioning-scheme> ::=
   PARTITION BY HASH  ( <column-name> [,... ] )
    SUBPARTITION BY <range-partition-scheme>
```

The hash partition specifies how the data is logically distributed and colocated; the range subpartition specifies how the data is physically placed. The new range subpartition is logically partitioned by hash with the same hash partition keys as the existing hash-range partitioned table. The range subpartition key is restricted to one column.

Restrictions:

-   You cannot add, drop, merge, or split a hash partition.
-   You cannot add or drop a column from a hash partition key.



</dd>
</dl>



</dd><dt><b>

SUBPARTITION BY RANGE

</b></dt>
<dd>

Subpartitions an existing hash-partition table.



</dd>
<dd>

```
SUBPARTITION BY <range-partition-decl>
```

Subpartitions on a range-partitioned table are not supported.



</dd><dt><b>

ADD \{PARTITION|SUBPARTITION\} BY RANGE

</b></dt>
<dd>

Adds a new partition to an existing range-partition table or a new subpartition to an existing hash range-partition table.

```
ADD { PARTITION | SUBPARTITION } BY RANGE <range-partition-decl>
```

The value of the *<range-partition-decl\>* must exceed the existing partition boundary. Only one partition or subpartition can be added per ADD clause. Use SPLIT PARTITION to add a range within the existing boundary.



</dd><dt><b>

UNPARTITION

</b></dt>
<dd>

Removes all partitions and subpartitions from a partitioned table. You cannot unpartition a subpatition only. ALTER TABLE UNPARTITION blocks all database activities.



</dd>
</dl>



<a name="loio816945966ce210149a80b8603addbc83__section_ow2_stk_sqb"/>

## Remarks

If you alter a materialized view owned by another user, you must qualify the name by including the owner \(for example, GROUPO.EmployeeConfidential\). If you don't qualify the name, the database server looks for a materialized view with that name owned by you and alters it. If there'sn't one, it returns an error.

When you disable a materialized view \(DISABLE clause\), it'sis no longer available for the database server to use for answering queries. As well, the data and indexes are dropped, and the refresh type changes to manual. Any dependent regular views are also disabled.

The DISABLE clause requires exclusive access not only to the view being disabled, but to any dependent views, since they're also disabled.

The only operations a user can perform on a materialized view to change its data are refreshing, truncating, and disabling.

Before you can execute DDL statements on base tables of `INCREMENTAL` refresh materialized views, you must first truncate the materialized view. Once the DDL statements are complete, you must manually refresh the materialized view.

```
TRUNCATE MATERIALIZED VIEW <materialized view name>;
<Execute DDL statements on the base table>;
REFRESH MATERIALIZED VIEW <materialized view name>;
```

Failure to truncate before executing DDL statements generates a message indicating that the table referenced by the DDL has versions pinned by pin requests, and the DDL fails. Pin Requests Management is an internal feature that facilitates INCREMENTAL refreshes.



<a name="loio816945966ce210149a80b8603addbc83__section_pxc_dbq_wwb"/>

## Privileges



### 

Requires one of:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loio816945966ce210149a80b8603addbc83__section_xph_vtk_sqb"/>

## Side Effects

-   Automatic commit.




<a name="loio816945966ce210149a80b8603addbc83__section_e4w_vtk_sqb"/>

## Standards


<dl>
<dt><b>

ANSI/ISO SQL Standard

</b></dt>
<dd>

Not in the standard.



</dd>
</dl>



## Examples

> ### Caution:  
> When you done with these examples, you should drop the materialized views you created. Otherwise, you may be unable to make schema changes to its underlying tables when trying out other examples. You can't alter the schema of a table that has an enabled, dependent materialized view configured for incremental refresh.

-   The following examples use several ALTER MATERIALIZED VIEW clauses to move, split, rename, and merge range- and hash-range partitions. The examples use the base table:

    ```
    CREATE TABLE BAR (C1 INT, C2 DATE, C3 VARCHAR(10), C4 INT NOT NULL, C5 BINARY);
    ```

    -   This syntax creates materialized view V\_BAR1 on table BAR:

        ```
        CREATE MATERIALIZED VIEW V_BAR1 AS SELECT C1, C2, C3 FROM BAR;
        ```

    -   This syntax range-partitions the materialized view:

        ```
        ALTER MATERIALIZED VIEW V_BAR1 PARTITION BY RANGE(C2)
              (P1 VALUES <= ('2005-12-31'),
               P2 VALUES <= ('2006-12-31'),
               P3 VALUES <= ('2007-12-31'));
        ```

    -   This syntax adds a fourth value range \(P4\) to the range-partition table:

        ```
        ALTER MATERIALIZED VIEW V_BAR1 ADD PARTITION BY RANGE (C2)
              (P4 VALUES <= ('2008-12-31'));
        ```

    -   This syntax initializes the materialized view V\_BAR1:

        ```
        REFRESH MATERIALIZED VIEW V_BAR1;
        ```

    -   This syntax splits partition P4 into two partitions:

        ```
        ALTER MATERIALIZED VIEW V_BAR1 SPLIT PARTITION P4 INTO 
           (P4a VALUES <= ('2008-06-30'),
            P4b VALUES <= ('2008-12-31'));
        ```

    -   This syntax reports an error, because it changes the partition boundary value:

        ```
        ALTER MATERIALIZED VIEW V_BAR1 SPLIT PARTITION P2 INTO 
           (P2a VALUES <= ('2006-06-30'),
            P2b VALUES <= ('2006-12-01'));
        ```

        This error is reported:

        ```
        Boundary value for the partition P2 cannot be changed.
        ```

    -   This syntax merges partition P3 into P2:

        ```
        ALTER MATERIALIZED VIEW V_BAR1 MERGE PARTITION P3 INTO P2;
        ```

        This error is reported, as a merge from a higher boundary value partition into a lower boundary value partition isn’t allowed:

        ```
        Partition 'P2' is not adjacent to or before partition 'P3'.
        ```

    -   This syntax merges partition P2 into P3:

        ```
        ALTER MATERIALIZED VIEW V_BAR1 MERGE PARTITION P2 INTO P3;
        ```

    -   This syntax renames partition P1 to P1\_NEW:

        ```
        ALTER MATERIALIZED VIEW V_BAR1 RENAME PARTITION P1 TO P1_NEW;
        ```

    -   This syntax unpartitions the materialized view:

        ```
        ALTER MATERIALIZED VIEW V_BAR1 UNPARTITION;
        ```

    -   This syntax hash-partitions materialized view:

        ```
        ALTER MATERIALIZED VIEW V_BAR1 PARTITION BY HASH(C1);
        ```

    -   This syntax subpartitions the hash-partition materialized view:

        ```
        ALTER MATERIALIZED VIEW V_BAR1 SUBPARTITION BY RANGE (C2)
              (P1 VALUES <= ('2005-12-31'),
               P2 VALUES <= ('2006-12-31'),
               P3 VALUES <= ('2007-12-31'));
        ```

    -   This syntax adds a fourth subpartition \(P4\) to the hash-range partition to materialized view:

        ```
        ALTER MATERIALIZED VIEW V_BAR1 ADD SUBPARTITION BY RANGE (C2)
              (P4 VALUES <= ('2008-12-31'));
        ```

    -   This syntax splits subpartition P2 into two partitions:

        ```
        ALTER MATERIALIZED VIEW V_BAR1 SPLIT SUBPARTITION P2 INTO 
           (P2a VALUES <= ('2006-06-30'),
            P2b VALUES <= ('2006-12-31'));
        ```


-   The following examples create a materialized view named V\_BAR2 using base table BAR and then its definition is hidden.

    -   This syntax creates the materialized view V\_BAR2.

        ```
        CREATE MATERIALIZED VIEW V_BAR2 AS SELECT C1, C3 FROM BAR;
        ```

    -   This syntax hides the materialized view definition.

        ```
        ALTER MATERIALIZED VIEW V_BAR2 SET HIDDEN;
        ```


-   The following examples create materialized view V\_BAR3 using table BAR. A unique index must be created on the non-nullable column C4 before the view can be configured to use incremental refresh.

    -   This syntax creates materialized view V\_BAR3 on table BAR configured for FULL automatic refresh:

        ```
        CREATE MATERIALIZED VIEW V_BAR3 AS SELECT C2, C3, C4 FROM BAR AUTO FULL REFRESH;
        ```

    -   This syntax creates a unique index on the non-nullable column C4:

        ```
        CREATE UNIQUE INDEX V_BAR3_IDX ON V_BAR3(C4);
        ```

    -   This syntax alters the materialized view to use automatic, INCREMENTAL refresh.

        ```
        ALTER MATERIALIZED VIEW V_BAR3 AUTO INCREMENTAL REFRESH;
        ```



**Related Information**  


[CREATE MATERIALIZED VIEW Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](create-materialized-view-statement-for-data-lake-relational-engine-sap-hana-db-managed-816c0ee.md "Creates a materialized view.")

[ALTER MATERIALIZED VIEW Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/d958953e260d44209300f5454e01029f.html "Alters a materialized view.") :arrow_upper_right:

[DROP Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](drop-statement-for-data-lake-relational-engine-sap-hana-db-managed-367d71d.md "Removes objects from the database.")

[Refresh and Build Types for Materialized Views in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2023_1_QRC/en-US/30ca3ca6ffbc4e6e804959f02571e62c.html "You can control when (refresh type): MANUAL or AUTO and how (build type): FULL or INCREMENTAL a materialized view is refreshed.") :arrow_upper_right:

