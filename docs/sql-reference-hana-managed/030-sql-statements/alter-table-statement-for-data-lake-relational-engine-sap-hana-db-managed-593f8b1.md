<!-- loio593f8b1caaaf4d31abc4a5a095d86254 -->

# ALTER TABLE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Modifies a table definition.



## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:

-   Connected to SAP HANA database as a SAP HANA database user..





### 

```
ALTER TABLE [ <schema-name>.]<table-name>
   ADD <create-column>
   | ALTER <column-name> <column-alteration>
   | ALTER [ CONSTRAINT <constraint-name> ] CHECK ( <condition> ) 
   | DROP <drop-object> 
   | RENAME <rename-object>
   | SPLIT { PARTITION | SUBPARTITION } <split-object>
   | MERGE { PARTITION | SUBPARTITION } <partition-name-1> INTO <partition-name-2> 
   | PARTITION BY <range-partitioning-scheme>  
            | <hash-partitioning-scheme> 
            | <hash-range-partitioning-scheme>
   | SUBPARTITION BY RANGE <range-partition-decl>
   | ADD { PARTITION | SUBPARTITION } BY RANGE <range-partition-decl>
   | UNPARTITION
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio593f8b1caaaf4d31abc4a5a095d86254__section_utk_zyk_sqb"/>

## Parameters



### *<create-column\>*


<dl>
<dt><b>



</b></dt>
<dd>

Adds a new column or column constraint to the table object.

```
<create-column> ::= 
   <column-name> <column-definition> [ <column-constraint> ]
   | <table-constraint>;
```


<dl>
<dt><b>

*<column-definition\>*

</b></dt>
<dd>

Defines a table column. Two columns in the same table cannot have the same name. You can create up to 45,000 columns; however, there might be performance penalties in tables with more than 10,000 columns.

```
<column definition> ::= 
   <data-type> [ NOT NULL | NULL  ] 
    [ IN <dbspace-name> ] 
    [ DEFAULT <default-value> | IDENTITY ];
```



</dd><dt><b>

\[ NOT \] NULL

</b></dt>
<dd>

Includes or excludes NULL values. If NOT NULL is specified, or if the column is in a UNIQUE or PRIMARY KEY constraint, the column cannot contain any NULL values. The limit on the number of columns per table that allow NULLs is approximately 8\*\(database-page-size - 30\). The table must be empty to specify NOT NULL.



</dd><dt><b>

*<default-value\>*

</b></dt>
<dd>

Specifies a default value to be assigned to the column if an INSERT statement does not provide a value for the column. A DEFAULT value is used as the value of the column in any INSERT \(or LOAD\) statement that does not specify a column value.

```
<default-value> ::= 
   CURRENT { DATABASE | DATE | REMOTE USER | TIME | TIMESTAMP | USER |PUBLISHER )
   | <string> 
   | <global variable> 
   | [ - ] <number> 
   | ( <constant-expression> ) 
   | <built-in-function> ( <constant-expression> ) 
   | AUTOINCREMENT 
   | NULL 
   | TIMESTAMP 
   | LAST USER 
   | USER;
```



</dd><dt><b>

IDENTITY/DEFAULT AUTOINCREMENT

</b></dt>
<dd>

Specifies the value of the IDENTITY/DEFAULT AUTOINCREMENT column, which uniquely identifies every row in a table.

The IDENTITY/DEFAULT AUTOINCREMENT column stores sequential numbers that are automatically generated during inserts and updates. DEFAULT AUTOINCREMENT columns are also known as IDENTITY columns. When using IDENTITY/DEFAULT AUTOINCREMENT, the column must be one of the integer data types, or an exact numeric type, with scale 0. See *CREATE TABLE Statement for Data Lake Relational Engine* for more about column constraints and IDENTITY/DEFAULT AUTOINCREMENT columns.

> ### Note:  
> The database option IDENTITY\_INSERT must be set to the table name to perform an explicit insert or update into an IDENTITY or AUTOINCREMENT column. For information on identity columns, see *The IDENTITY or AUTOINCREMENT Default* in *SAP HANA Cloud, Data Lake Administration Guide for Data Lake Relational Engine*.



</dd><dt><b>

*<table-constraint\>* and *<column-constraint\>*

</b></dt>
<dd>

See *<table-constraint\>* and *<column-constraint\>* in *CREATE TABLE Statement for Data Lake Relational Engine*.



</dd>
</dl>



</dd>
</dl>



### *<column-alteration\>*


<dl>
<dt><b>



</b></dt>
<dd>

Changes the column definition.

```
<column-alteration> ::= 
   { <column-data-type> | <alterable-column-attribute> } [ <alterable-column-attribute> … ]  
    | ADD [ CONSTRAINT[ <constraint-name> ] CHECK ( <condition> )  
    | DROP { DEFAULT | CHECK | CONSTRAINT <constraint-name> };
```

```
<alterable-column-attribute> ::=
   [ NOT ] NULL 
   | DEFAULT <default-value>  
   | [ CONSTRAINT <constraint-name> ] CHECK { NULL | ( <condition> ) 
     };
```


<dl>
<dt><b>

SET DEFAULT *<default-value\>*

</b></dt>
<dd>

Changes the default value of an existing column in a table. You can also use the MODIFY clause for this task, but ALTER is ISO/ANSI SQL compliant, and MODIFY is not. Modifying a default value does not change any existing values in the table.



</dd><dt><b>

CONSTRAINT *<column-constraint-name\>*

</b></dt>
<dd>

The optional column constraint name lets you modify or drop individual constraints at a later time, rather than having to modify the entire column constraint.



</dd><dt><b>

\[CONSTRAINT *<constraint-name\>*\] CHECK \(*<condition\>*\)

</b></dt>
<dd>

Adds a CHECK constraint on the column.



</dd><dt><b>

ADD

</b></dt>
<dd>

Adds a named constraint or a CHECK condition to the column. The new constraint or condition applies only to operations on the table after its definition. The existing values in the table are not validated to confirm that they satisfy the new constraint or condition.



</dd><dt><b>

DROP DEFAULT

</b></dt>
<dd>

Removes the default value of an existing column in a table. You can also use the MODIFY clause for this task, but ALTER is ISO/ANSI SQL compliant, and MODIFY is not. Dropping a default does not change any existing values in the table.



</dd>
</dl>



</dd>
</dl>



### DROP *<drop-object\>*


<dl>
<dt><b>



</b></dt>
<dd>

Drops a table object.

```
<drop-object> ::= 
   <column-name> 
   | CHECK <constraint-name>
   | CONSTRAINT  
   | UNIQUE ( <index-columns-list> )  
   | PRIMARY KEY 
   | FOREIGN KEY <fkey-name>
   | { PARTITION | SUBPARTITION } <range-partition-name>;
```


<dl>
<dt><b>

DROP *<column-name\>*

</b></dt>
<dd>

Drops the column from the table. If the column is contained in any multicolumn index, uniqueness constraint, foreign key, or primary key, then the index, constraint, or key must be deleted before the column can be deleted. This does not delete CHECK constraints that refer to the column. An IDENTITY/DEFAULT AUTOINCREMENT column can only be deleted if IDENTITY\_INSERT is turned off and the table is not a local temporary table.



</dd><dt><b>

DROP CHECK

</b></dt>
<dd>

Drops all check constraints for the table. This includes both table check constraints and column check constraints.



</dd><dt><b>

DROP CONSTRAINT *<constraint-name\>*

</b></dt>
<dd>

Drops the named constraint for the table or specified column.



</dd><dt><b>

DROP UNIQUE \( *<column-name, ...\>* \)

</b></dt>
<dd>

Drops the unique constraints on the specified column\(s\). Any foreign keys referencing the unique constraint \(rather than the primary key\) are also deleted. Reports an error if there are associated foreign-key constraints. Use ALTER TABLE to delete all foreign keys that reference the primary key before you delete the primary key constraint.



</dd><dt><b>

DROP PRIMARY KEY

</b></dt>
<dd>

Drops the primary key. All foreign keys referencing the primary key for this table are also deleted. Reports an error if there are associated foreign key constraints. If the primary key is unenforced, DELETE returns an error if associated unenforced foreign key constraints exist.



</dd><dt><b>

DROP FOREIGN KEY *<role-name\>*

</b></dt>
<dd>

Drops the foreign key constraint for this table with the given role name. Retains the implicitly created non-unique HG index for the foreign key constraint. Users can explicitly remove the HG index with the DROP INDEX statement.



</dd><dt><b>

DROP \{ PARTITION | SUBPARTITION \}\]

</b></dt>
<dd>

Drops the specified partition or subpartition. The rows in the partition or subpartition are deleted and the definition is dropped. You cannot drop the last partition because dropping the last partition would transform a partitioned table to a non-partitioned table. You cannot drop the last subpartition. To merge a partitioned table, use an UNPARTITION clause instead.



</dd>
</dl>



</dd>
</dl>



### RENAME *<rename-object\>*


<dl>
<dt><b>



</b></dt>
<dd>

Renames an object in the table.

```
<rename-object> ::= 
   <new-table-name>  
   | <column-name> TO <new-column-name>   
   | CONSTRAINT <constraint-name> TO <new-constraint-name> 
   | { PARTITION | SUBPARTITION } <range-partition-name> TO <new-range-partition-name>;
```


<dl>
<dt><b>

RENAME *<new-table-name\>*

</b></dt>
<dd>

Changes the name of the table to the *<new-table-name\>*. Any applications using the old table name must be modified. Also, any foreign keys that were automatically assigned the same name as the old table name do not change names.



</dd><dt><b>

RENAME *<column-name\>* TO *<new-column-name\>*

</b></dt>
<dd>

Changes the name of the column to *<new-column-name\>*. Any applications using the old column name must be modified.



</dd><dt><b>

RENAME *<constraint-name\>* TO *<new-constraint-name\>*

</b></dt>
<dd>

Changes the name of the constraint to *<new-constraint-name\>*. Any applications using the old constraint name must be modified.



</dd><dt><b>

RENAME \{ PARTITION | SUBPARTITON \}

</b></dt>
<dd>

Changes the name of an existing partition or sub-partition.



</dd>
</dl>



</dd>
</dl>



### SPLIT \{ PARTITION | SUBPARTITION \} *<split-object\>*


<dl>
<dt><b>



</b></dt>
<dd>

Splits an existing range partition or subpartition.

```
<split-object> ::= <range-partition-decl> 
        INTO ( <range-partition-decl>, <range-partition-decl> );
```

When splitting a partition or subpartition, the names of the new partitions must be unique and cannot include the name of the original partition. All data from the original partition must fit into only one of the resulting partitions. Data cannot move between partitions.

When splitting a partition or subpartition, the upper boundary of the new partitions must be equal to the upper boundary of the original partition. For example, if P1 has a boundary of 100 and you split P1 into P1A and P1B, the boundary of P1B must be 100.



</dd>
</dl>



### MERGE \{ PARTITION | SUBPARTITION\}


<dl>
<dt><b>



</b></dt>
<dd>

Merges *<partition-name-1\>* into *<partition-name-2\>*. Two partitions can be merged if they are adjacent partitions. You can only merge a partition with a lower partition value into the adjacent partition with a higher partition value. Note that the server does not check CREATE privilege into which the partition is merged. For an example of how to create adjacent partitions, see CREATE TABLE Statement examples.



</dd>
</dl>



### PARTITION BY


<dl>
<dt><b>



</b></dt>
<dd>

Divides large tables into smaller, more manageable storage objects. Partitions share the same logical attributes of the parent table, but can be placed in separate dbspaces and managed individually. Data lake Relational Engine supports several table partitioning schemes:

-   Range-partitions
-   Hash-partitions
-   Hash range-partitions

A partition-key is the column or columns that contain the table partitioning keys. Partition keys can contain NULL and DEFAULT values, but cannot contain:

-   LOB \(BLOB or CLOB\) columns
-   BINARY, or VARBINARY columns
-   CHAR or VARCHAR columns that are 255 bytes long
-   BIT columns
-   FLOAT/DOUBLE/REAL columns



</dd>
<dd>

Restrictions when partitioning an existing table:

-   For range partitioning, all existing data in the table must exist within the upper bound of the first partition of the table.
-   For hash partitioning and range subpartitioning of a hash table, the table must be empty.



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
   RANGE ( <column_name> ) ( <range-partition-decl> [,...] );
```


<dl>
<dt><b>

*<range-partition-decl\>*

</b></dt>
<dd>

```
<range-partition-decl> ::=
   <partition-name> VALUES <= ( { <constant-expression> | MAX } [,...] );
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
           (P1 VALUES <=(CAST (1 AS VARCHAR(20))), P2 VALUES <= (CAST (10 AS VARCHAR(20)));
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
   HASH ( <column_name> [,... ] );
```

In a hash-partitioning declaration, the partition-key is a column or group of columns, whose composite value determines the partition where each row of data is stored:

```
hash-partitioning-scheme: 
  HASH  ( <partition-key> [ , <partition-key>, … ] );
```

Restrictions:

-   You can only hash partition a base table. Attempting to partitioning a global temporary table or a local temporary table raises an error.
-   You cannot add, drop, merge, or split a hash partition.
-   You cannot add or drop a column from a hash partition key.



</dd><dt><b>

*<hash-range-partitioning-scheme\>*

</b></dt>
<dd>

Maps data to partitions based on partition-key values processed by an internal hashing function and subpartitions the hash-partitioned table by range.

```
<hash-range-partitioning-scheme> ::=
   PARTITION BY HASH  ( <column_name> [,... ] )
    SUBPARTITION BY <range-partition-scheme>;
```

The hash partition specifies how the data is logically distributed and colocated; the range subpartition specifies how the data is physically placed. The new range subpartition is logically partitioned by hash with the same hash partition keys as the existing hash-range partitioned table. The range subpartition key is restricted to one column.

Restrictions:

-   You can only hash partition a base table. Attempting to partitioning a global temporary table or a local temporary table raises an error.
-   You can only subpartition a hash-partitioned table by range if the table is empty.
-   You cannot add, drop, merge, or split a hash partition.
-   You cannot add or drop a column from a hash partition key.



</dd>
</dl>



</dd>
</dl>



### SUBPARTITION BY RANGE


<dl>
<dt><b>



</b></dt>
<dd>

Subpartitions an existing hash-partition table.



</dd>
<dd>

```
SUBPARTITION BY <range-partition-decl>;
```

Subpartitions on a range-partitioned table are not supported.



</dd>
</dl>



### ADD \{PARTITION|SUBPARTITION\} BY RANGE


<dl>
<dt><b>



</b></dt>
<dd>

Adds a new partition to an existing range-partition table or a new subpartition to an existing hash range-partition table.

```
ADD { PARTITION | SUBPARTITION } BY RANGE <range-partition-decl>;
```

The value of the *<range-partition-decl\>* must exceed the existing partition boundary. Only one partition or subpartition can be added per ADD clause. Use SPLIT PARTITION to add a range within the existing boundary.



</dd>
</dl>



### UNPARTITION


<dl>
<dt><b>



</b></dt>
<dd>

Removes all partitions and subpartitions from a partitioned table. You cannot unpartition a subpatition only. ALTER TABLE UNPARTITION blocks all database activities.



</dd>
</dl>



<a name="loio593f8b1caaaf4d31abc4a5a095d86254__section_z2z_1zk_sqb"/>

## Remarks

The ALTER TABLE statement changes table attributes \(column definitions and constraints\) in a table that was previously created. The syntax allows a list of alter clauses; however, only one table constraint or column constraint can be added, modified, or deleted in each ALTER TABLE statement. ALTER TABLE is prevented whenever the statement affects a table that is currently being used by another connection. ALTER TABLE can be time consuming, and the server does not process requests referencing the same table while the statement is being processed.

> ### Note:  
> You cannot alter local temporary tables, but you can alter global temporary tables when they are in use by only one connection.

-   Column
-   Primary key
-   Foreign key
-   Range partition \(adding and splitting\)

Data lake Relational Engine enforces REFERENCES and CHECK constraints. Table and/or column check constraints added in an ALTER TABLE statement are evaluated, only if they are defined on one of the new columns added, as part of that alter table operation. For details about CHECK constraints, see *CREATE TABLE Statement*.

If SELECT *<\*\>* is used in a view definition and you alter a table referenced by the SELECT *<\*\>* , then you must run ALTER VIEW *<viewname\>* RECOMPILE to ensure that the view definition is correct and to prevent unexpected results when querying the view.



<a name="loio593f8b1caaaf4d31abc4a5a095d86254__section_xv3_42q_wwb"/>

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
<dd>

To move a table between relational containers \(for example, from SYSHDL\_CONTAINER1 to SYSHDL\_CONTAINER2\), also requires:

-   You are a member of the relational container administration role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), containing the table being moved \(source relational container\).
-   The ALTER object-level privilege on therelational container schema in the destination relational container is granted to the container administrator role of the source relational container.



</dd>
</dl>



<a name="loio593f8b1caaaf4d31abc4a5a095d86254__section_lwm_dzk_sqb"/>

## Side Effects

-   Automatic commit. The ALTER and DROP options close all cursors for the current connection. The Interactive SQL data window is also cleared.
-   A checkpoint is carried out at the beginning of the ALTER TABLE operation.
-   Once you alter a column or table, any stored procedures, views or other items that refer to the altered column no longer work.



<a name="loio593f8b1caaaf4d31abc4a5a095d86254__section_tjz_2zk_sqb"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – some clauses are supported by SAP Adaptive Server Enterprise.



<a name="loio593f8b1caaaf4d31abc4a5a095d86254__section_zcc_hzk_sqb"/>

## Examples

-   The following example adds a new column to the Employees table showing which office they work in:

    ```
    ALTER TABLE EMPLOYEES ADD OFFICE VARCHAR(20);
    ```

-   The following example drops the office column from the Employees table:

    ```
    ALTER TABLE EMPLOYEES DROP OFFICE;
    ```

-   The following example adds a column to the Customers table assigning each customer a sales contact:

    ```
    ALTER TABLE CUSTOMERS ADD SALESCONTACT INTEGER
       REFERENCES EMPLOYEE(EMPLOYEEID);
    ```

-   The following example adds a new column CUSTOMERNUM to the Customers table and assigns a default value of 88:

    ```
    ALTER TABLE CUSTOMERS ADD CUSTOMERNUM INTEGER DEFAULT 88;
    ```

-   The following example uses many ALTER TABLE clauses to move, split, rename, and merge range- partitions.

    Create a table:

    ```
    CREATE TABLE BAR (C1 INT, C2 DATE, C3 VARCHAR(10));
    ```

-   -   This example range-partitions the table:

    ```
    ALTER TABLE BAR PARTITION BY RANGE(C2)
          (P1 VALUES <= ('2005-12-31'),
           P2 VALUES <= ('2006-12-31'),
           P3 VALUES <= ('2007-12-31'));
    ```

-   This example adds a fourth value range \(P4\) to the range-partition table:

    ```
    ALTER TABLE BAR ADD PARTITION BY RANGE (C2)
          (P4 VALUES <= ('2008-12-31'));
    ```

-   This example splits partition P4 into two partitions:

    ```
    ALTER TABLE BAR SPLIT PARTITION P4 INTO 
       (P41 VALUES <= ('2008-06-30'),
        P42 VALUES <= ('2008-12-31'));
    ```

-   This example reports an error, because it changes the partition boundary value:

    ```
    ALTER TABLE BAR SPLIT PARTITION P2 INTO 
       (P21 VALUES <= ('2006-06-30'),
        P22 VALUES <= ('2006-12-01'));
    ```

    This error is reported:

    ```
    Boundary value for the partition P2 cannot be changed.
    ```

-   This example merges partition P3 into P2:

    ```
    ALTER TABLE BAR MERGE PARTITION P3 INTO P2;
    ```

    This error is reported, as a merge from a higher boundary value partition into a lower boundary value partition isn’t allowed:

    ```
    Partition 'P2' is not adjacent to or before partition 'P3'.
    ```

-   This example merges partition P2 into P3:

    ```
    ALTER TABLE BAR MERGE PARTITION P2 INTO P3;
    ```

-   This example renames partition P1 to P1\_NEW:

    ```
    ALTER TABLE BAR RENAME PARTITION P1 TO P1_NEW;
    ```

-   This example unpartitions table BAR:

    ```
    ALTER TABLE BAR UNPARTITION;
    ```

-   This example hash-partitions table BAR:

    ```
    ALTER TABLE BAR PARTITION BY HASH(C1);
    ```

-   This example subpartitions the hash-partition table BAR:

    ```
    ALTER TABLE BAR SUBPARTITION BY RANGE (C2)
          (P1 VALUES <= ('2005-12-31'),
           P2 VALUES <= ('2006-12-31'),
           P3 VALUES <= ('2007-12-31'));
    ```

-   This example adds a fourth value subpartition \(P4\) to the hash-range partition table:

    ```
    ALTER TABLE BAR ADD SUBPARTITION BY RANGE (C2)
          (P4 VALUES <= ('2008-12-31'));
    ```

-   This example splits subpartition P2 into two partitions:

    ```
    ALTER TABLE BAR SPLIT SUBPARTITION P2 INTO 
       (P2a VALUES <= ('2006-06-30'),
        P2b VALUES <= ('2006-12-31'));
    ```



**Related Information**  


[CREATE TABLE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](create-table-statement-for-data-lake-relational-engine-sap-hana-db-managed-6c3afae.md "Creates a new table in the database or on a remote server.")

[DROP TABLE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](drop-table-statement-for-data-lake-relational-engine-sap-hana-db-managed-1e62d19.md "Removes a table from the database.")

[Moving a Table Between Schemas and Relational Containers](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2024_1_QRC/en-US/7cc5b90e27e145aa9542a7a494bd61ef.html "Move a data lake Relational Engine physical table between schemas in the same relational container or between relational containers.") :arrow_upper_right:

[Data Types Compatibility with SAP HANA Database for the CREATE TABLE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](data-types-compatibility-with-sap-hana-database-for-the-create-table-statement-for-data-l-e77d888.md "The data lake Relational Engine CREATE TABLE statement lets you create a data lake Relational Engine physical table.")

[ALTER TABLE Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/39f1ec0fd2c9451c8b64df54efe48a03.html "Modifies a table definition.") :arrow_upper_right:

