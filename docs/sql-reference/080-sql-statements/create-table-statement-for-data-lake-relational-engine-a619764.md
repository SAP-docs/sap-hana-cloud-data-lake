<!-- loioa619764084f21015b8039a8346dc622c -->

# CREATE TABLE Statement for Data Lake Relational Engine 

Creates a new table in the database or on a remote server.



<a name="loioa619764084f21015b8039a8346dc622c__section_azh_5fj_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
CREATE [ { GLOBAL | LOCAL } TEMPORARY ] TABLE
   [ IF NOT EXISTS ] [ { <owner> | <schema-name> }.]<table-name>
   … ( <column-definition> [ <column-constraint> ] ...
   [, <column-definition> [ <column-constraint> ] ...]
   [, <table-constraint> [,...])
   [ ON COMMIT { DELETE | PRESERVE } ROWS ]
   [ AT <location-string> ]
   [PARTITION BY 
     { <range-partitioning-scheme>
     | <hash-partitioning-scheme> 
     | <hash-range-partitioning-scheme> ] };
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa619764084f21015b8039a8346dc622c__create_table_parameters1"/>

## Parameters



### IF NOT EXISTS


<dl>
<dt><b>



</b></dt>
<dd>

If the named object already exists, no changes are made and an error is not returned.



</dd>
</dl>



### *<column-definition\>*


<dl>
<dt><b>



</b></dt>
<dd>

Defines a table column. Allowable data types are described in *Data Types*. Two columns in the same table cannot have the same name. You can create up to 45,000 columns; however, there might be performance penalties in tables with more than 10,000 columns:

```
<column-definition> ::=
   <column-name> <data-type> 
    [ [ NOT ] NULL ] 
    [ { DEFAULT <default-value> | IDENTITY } ];
```


<dl>
<dt><b>

*<data-type\>*

</b></dt>
<dd>

For a list of supported data types, see [Available Data Types for CREATE TABLE in Data Lake Relational Engine](available-data-types-for-create-table-in-data-lake-relational-engine-4ef997d.md).



</dd><dt><b>

\[ NOT \] NULL

</b></dt>
<dd>

Includes or excludes NULL values. If NOT NULL is specified, or if the column is in a UNIQUE or PRIMARY KEY constraint, the column cannot contain any NULL values. The limit on the number of columns per table that allow NULLs is approximately 8\*\(database-page-size - 30\). The table must be empty to specify NOT NULL. By default, columns declared as BIT are created as NOT NULL, but they can be explicitly declared as NULL.



</dd><dt><b>

*<default\_value\>*

</b></dt>
<dd>

Specifies a default value to be assigned to the column if an INSERT statement does not provide a value for the column. A DEFAULT value is used as the value of the column in any INSERT \(or LOAD\) statement that does not specify a column value.

```
<default-value> ::=
   <special-value>
   | <string>
   | <global variable>
   | [ - ] <number>
   | ( <constant-expression> )
   | <built-in-function>( <constant-expression> )
   | AUTOINCREMENT
   | CURRENT DATABASE
   | CURRENT REMOTE USER
   | NULL
   | TIMESTAMP
   | LAST USER
```

```
<special-value> ::=
   CURRENT 
   { DATE | TIME | TIMESTAMP | USER | PUBLISHER }
   | USER;
```



</dd><dt><b>

AUTOINCREMENT

</b></dt>
<dd>

DEFAULT AUTOINCREMENT – The value of the DEFAULT AUTOINCREMENT column uniquely identifies every row in a table. Columns of this type are also known as IDENTITY columns, for compatibility with SAP Adaptive Server Enterprise.

The IDENTITY/DEFAULT AUTOINCREMENT column stores sequential numbers that are automatically generated during inserts and updates. When using IDENTITY or DEFAULT AUTOINCREMENT, the column must be one of the integer data types, or an exact numeric type, with scale 0. The column value might also be NULL. Qualify the specified table name with the owner name.



</dd><dt><b>

IDENTITY

</b></dt>
<dd>

A Transact-SQL-compatible alternative to using the AUTOINCREMENT default. In data lake Relational Engine, the identity column may be created using either the IDENTITY or the DEFAULT AUTOINCREMENT clause.



</dd>
</dl>



</dd>
</dl>



### *<table-constraint\>*


<dl>
<dt><b>



</b></dt>
<dd>

Helps ensure the integrity of data in the database. There are four types of integrity constraints:

-   UNIQUE – identifies one or more columns that uniquely identify each row in the table. No two rows in the table can have the same values in all the named columns. A table may have more than one unique constraint.

-   PRIMARY KEY – the same as a UNIQUE constraint except that a table can have only one primary-key constraint. You cannot specify the PRIMARY KEY and UNIQUE constraints for the same column. The primary key usually identifies the best identifier for a row. For example, the customer number might be the primary key for the customer table.

-   FOREIGN KEY – restricts the values for a set of columns to match the values in a primary key or uniqueness constraint of another table. For example, a foreign-key constraint could be used to ensure that a customer number in an invoice table corresponds to a customer number in the customer table.

    You cannot create foreign-key constraints on local temporary tables. Global temporary tables must be created with ON COMMIT PRESERVE ROWS.

-   CHECK – allows arbitrary conditions to be verified. For example, a check constraint could be used to ensure that a column called Gender contains only the values male or female. No row in a table is allowed to violate a constraint. If an INSERT or UPDATE statement would cause a row to violate a constraint, the operation is not permitted and the effects of the statement are undone.

    Column identifiers in column check constraints that start with the symbol ‘@’ are placeholders for the actual column name. The following two statements are exactly the same:

    ```
    CREATE TABLE t1(c1 INTEGER CHECK (@foo < 5));
    ```

    ```
    CREATE TABLE t1(c1 INTEGER CHECK (c1 < 5));
    ```

    Column identifiers appearing in table check constraints that start with the symbol ‘@’are not placeholders.


If a statement would cause changes to the database that violate an integrity constraint, the statement is effectively not executed and an error is reported. This means that any changes made by the statement before the error was detected are undone.

Data lake Relational Engine enforces single-column UNIQUE constraints by creating an HG index for that column.

> ### Note:  
> You cannot define a column with a BIT data type as a UNIQUE or PRIMARY KEY constraint. Also, the default for columns of BIT data type is to not allow NULL values; you can change this by explicitly defining the column as allowing NULL values.



</dd>
</dl>



### *<column-constraint\>*


<dl>
<dt><b>



</b></dt>
<dd>

Restricts the values the column can hold. Column and table constraints help ensure the integrity of data in the database. If a statement would cause a violation of a constraint, execution of the statement does not complete, any changes made by the statement before error detection are undone, and an error is reported. Column constraints are abbreviations for the corresponding table constraints. For example, these are equivalent:

```
CREATE TABLE Products (
	product_num integer UNIQUE
);
```

```
CREATE TABLE Products (
	product_num integer,
	UNIQUE ( product_num )
);
```

Column constraints are normally used unless the constraint references more than one column in the table. In these cases, use a table constraint.



</dd>
</dl>



### *<column-constraint\>* and *<table-constraint\>* clauses


<dl>
<dt><b>



</b></dt>
<dd>

Column and table constraints help ensure the integrity of data in the database.

```
<column-constraint> ::=
   IQ UNIQUE ( <integer> )
   | { [ CONSTRAINT <constraint-name> ] 
     { UNIQUE  
        | PRIMARY KEY  
        | REFERENCES <table-name> [ ( <column-name> ) ] [ ON { UPDATE | DELETE } RESTRICT ] }
      | CHECK ( <condition> )
   };
```

> ### Note:  
> Specifying a *<constraint-name\>* when using the IQ UNIQUE clause as a *<column-constraint\>* yields an error. For example,
> 
> ```
> CREATE TABLE T1 ( 
>     PRODUCT_ID INT NOT NULL, 
>     ORDER_ID INT NULL CONSTRAINT MYCONSTRAINT IQ UNIQUE (5000) 
> );
> ```
> 
> results in an error. Remove the *<constraint-name\>* to resolve the issue:
> 
> ```
> CREATE TABLE T1 ( 
>     PRODUCT_ID INT NOT NULL, 
>     ORDER_ID INT NULL IQ UNIQUE (5000) 
> );
> ```

```
<table-constraint> ::=
    [ CONSTRAINT <constraint-name> ] 
   {  { UNIQUE | PRIMARY KEY } ( <column-name> [ , … ] )  
     [ IN <dbspace-name> ]
     | <foreign-key-constraint>
     | CHECK ( <condition> )
   };
```


<dl>
<dt><b>

PRIMARY KEY or PRIMARY KEY \( *<column-name\>*, … \)

</b></dt>
<dd>

The primary key for the table consists of the listed columns, and none of the named columns can contain any NULL values. Data lake Relational Engine ensures that each row in the table has a unique primary key value. A table can have only one PRIMARY KEY.

When the second form is used \(PRIMARY KEY followed by a list of columns\), the primary key is created including the columns in the order in which they are defined, not the order in which they are listed.

When a column is designated as PRIMARY KEY, FOREIGN KEY, or UNIQUE, data lake Relational Engine creates a High\_Group index for it automatically. For multicolumn primary keys, this index is on the primary key, not the individual columns. For best performance, you should also index each column with an HG index separately.



</dd><dt><b>

REFERENCES *<primary-table-name\>* \[\(*<primary-column-name\>*\)\]

</b></dt>
<dd>

Defines the column as a foreign key for a primary key or a unique constraint of a primary table. Normally, a foreign key would be for a primary key rather than an unique constraint. If a primary column name is specified, it must match a column in the primary table, which is subject to a unique constraint or primary key constraint, and that constraint must consist of only that one column. Otherwise the foreign key references the primary key of the second table. Primary key and foreign key must have the same data type and the same precision, scale, and sign. Only a non-unique single-column HG index is created for a single-column foreign key. For a multi-column foreign key, data lake Relational Engine creates a non unique composite HG index. The maximum width of a multi-column composite key for a unique or non unique HG index is 1 KB.

A temporary table cannot have a foreign key that references a base table and a base table cannot have a foreign key that references a temporary table. Local temporary tables cannot have or be referenced by a foreign key.



</dd><dt><b>

ON

</b></dt>
<dd>

The action ON inserts into the table. If a value is not specified for the IDENTITY/DEFAULT AUTOINCREMENT column, a unique value larger than any other value in the column is generated. If an INSERT specifies a value for the column, it is used; if the specified value is not larger than the current maximum value for the column, that value is used as a starting point for subsequent inserts.

Deleting rows does not decrement the IDENTITY/AUTOINCREMENT counter. Gaps created by deleting rows can only be filled by explicit assignment when using an insert.

> ### Note:  
> To perform an explicit insert or update into an IDENTITY/AUTOINCREMENT column, set the IDENTITY\_INSERT database option to the table name.

For example, this creates a table with an IDENTITY column and explicitly adds some data to it:

```
CREATE TABLE mytable(c1 INT IDENTITY);
SET TEMPORARY OPTION IDENTITY_INSERT = 'JOE.mytable';
INSERT INTO mytable VALUES(5);
```

After an explicit insert of a row number less than the maximum, subsequent rows without explicit assignment are still automatically incremented with a value of one greater than the previous maximum.

You can find the most recently inserted value of the column by inspecting the @@identity global variable.



</dd><dt><b>

*<foreign-key-constraint\>*

</b></dt>
<dd>

Defines foreign-key references to a primary key or a unique constraint in another table. Normally, a foreign key would be for a primary key rather than an unique constraint. \(In this description, this other table is called the primary table.\)

```
<foreign-key-constraint> ::=
   FOREIGN KEY [ <role-name> ] [ ( <column-name> [ , <column-name> ] … ) ] 
   …REFERENCES <table-name> [ ( <column-name> [ , <column-name> ] … ) ]
   [ ON { UPDATE | DELETE } RESTRICT ];
```

If the primary table column names are not specified, the primary table columns are the columns in the table's primary key. If foreign key column names are not specified, the foreign-key columns have the same names as the columns in the primary table. If foreign-key column names are specified, then the primary key column names must be specified, and the column names are paired according to position in the lists.

If the primary table is not the same as the foreign-key table, either the unique or primary key constraint must have been defined on the referenced key. Both referenced key and foreign key must have the same number of columns, of identical data type with the same sign, precision, and scale.

The value of the row's foreign key must appear as a candidate key value in one of the primary table's rows unless one or more of the columns in the foreign key contains nulls in a null allows foreign key column.

Any foreign-key column not explicitly defined is automatically created with the same data type as the corresponding column in the primary table. These automatically created columns cannot be part of the primary key of the foreign table. Thus, a column used in both a primary key and foreign key must be explicitly created.


<dl>
<dt><b>

*<role-name\>*

</b></dt>
<dd>

1.  If there is no foreign key with a *<role-name\>* the same as the table name, the table name is assigned as the *<role-name\>*.
2.  If the table name is already taken, the *<role-name\>* is the table name concatenated with a zero-padded 3-digit number unique to the table.

The referential integrity action defines the action to be taken to maintain foreign-key relationships in the database. Whenever a primary key value is changed or deleted from a database table, there may be corresponding foreign key values in other tables that should be modified in some way. You can specify an ON DELETE clause, followed by the RESTRICT clause.



</dd><dt><b>

RESTRICT

</b></dt>
<dd>

Generates an error if you try to update or delete a primary key value while there are corresponding foreign keys elsewhere in the database. Generates an error if you try to update a foreign key so that you create new values unmatched by a candidate key. This is the default action, unless you specify that LOAD optionally reject rows that violate referential integrity. This enforces referential integrity at the statement level.

If you use CHECK ON COMMIT without specifying any actions, then RESTRICT is implied as an action for DELETE. Data lake Relational Engine does not support CHECK ON COMMIT.

A global temporary table cannot have a foreign key that references a base table and a base table cannot have a foreign key that references a global temporary table. Local temporary tables cannot have or be referenced by a foreign key.



</dd>
</dl>



</dd><dt><b>

CHECK \( *<condition\>* \)

</b></dt>
<dd>

Ensures that no row is allowed to fail the condition. If an INSERT statement would cause a row to fail the condition, the operation is not permitted and the effects of the statement are undone. The change is rejected only if the condition is FALSE; in particular, the change is allowed if the condition is UNKNOWN. CHECK condition is not enforced by data lake Relational Engine. If possible, do not define referential integrity foreign key-primary key relationships in data lake Relational Engine

unless you are certain there are no orphan foreign keys.



</dd><dt><b>

IQ UNIQUE

</b></dt>
<dd>

Defines the expected cardinality of a column and determines whether the column loads as Flat FP or NBit FP. An IQ UNIQUE\(n\) value explicitly set to 0 loads the column as Flat FP. Columns without an IQ UNIQUE constraint implicitly load as NBit up to the limits defined by the FP\_NBIT\_AUTOSIZE\_LIMIT, FP\_NBIT\_LOOKUP\_MB, and FP\_NBIT\_ROLLOVER\_MAX\_MB options:

-   FP\_NBIT\_AUTOSIZE\_LIMIT limits the number of distinct values that load as NBit
-   FP\_NBIT\_LOOKUP\_MB sets a threshold for the total NBit dictionary size
-   FP\_NBIT\_ROLLOVER\_MAX\_MB sets the dictionary size for implicit NBit rollovers from NBit to Flat FP
-   FP\_NBIT\_ENFORCE\_LIMITS enforces NBit dictionary sizing limits. This option is OFF by default

Using IQ UNIQUE with an n value less than the FP\_NBIT\_AUTOSIZE\_LIMIT is not necessary. Auto-size functionality automatically sizes all low or medium cardinality columns as NBit. Use IQ UNIQUE in cases where you want to load the column as Flat FP or when you want to load a column as NBit when the number of distinct values exceeds the FP\_NBIT\_AUTOSIZE\_LIMIT.



</dd>
</dl>

> ### Note:  
> -   Consider memory usage when specifying high IQ UNIQUE values. If machine resources are limited, avoid loads with FP\_NBIT\_ENFORCE\_LIMITS='OFF' \(default\).
> 
>     Prior to data lake Relational Engine 16.1, an IQ UNIQUE *<n\>* value \> 16777216 would rollover to Flat FP. In 16.1, larger IQ UNIQUE values are supported for tokenization, but may require significant memory resource requirements depending on cardinality and column width.
> 
> -   BIT, BLOB, and CLOB data types do not support NBit dictionary compression. If FP\_NBIT\_IQ15\_COMPATIBILITY=’OFF’, a non-zero IQ UNIQUE column specification in a CREATE TABLE or ALTER TABLE statement that includes these data types returns an error.



</dd>
</dl>



### ON COMMIT


<dl>
<dt><b>



</b></dt>
<dd>

Allowed for temporary tables only. By default, the rows of a temporary table are deleted on COMMIT.



</dd>
</dl>



### AT *<location-string\>*


<dl>
<dt><b>



</b></dt>
<dd>

Creates a proxy table that maps to a remote location specified by the location-string clause.

```
<location-string> ::=
   { <remote-server-name>. [ <db-name> ].[ <owner> ].<object-name>
      | <remote-server-name>; [ <db-name> ]; [ <owner> ];<object-name> };
```

Proxy table names must be 30 characters or less. The AT clause supports semicolon \(;\) delimiters. If a semicolon is present anywhere in the location-string clause, the semicolon is the field delimiter. If no semicolon is present, a period is the field delimiter. This allows file names and extensions to be used in the database and owner fields.

Semicolon field delimiters are used primarily with server classes not currently supported; however, you can also use them in situations where a period would also work as a field delimiter. For example, this statement maps the table proxy\_a to the SAP SQL Anywhere database mydb on the remote server myasa:

```
CREATE TABLE proxy_a1
AT 'myasa;mydb;;a1';
```

Foreign-key definitions are ignored on remote tables. Foreign-key definitions on local tables that refer to remote tables are also ignored. Primary key definitions are sent to the remote server if the server supports primary keys.

You cannot create a proxy table that refers to a remote table on the same node, nor can you create a proxy table that refers to the remote table defined within the multiplex.



</dd>
</dl>



### PARTITION BY


<dl>
<dt><b>



</b></dt>
<dd>

Divides large tables into smaller, more manageable storage objects. Data lake Relational Engine supports several table partitioning schemes:

-   Hash-partitions
-   Range-partitions
-   Hash range-partitions

A partition-key is the column or columns that contain the table partitioning keys. Partition keys can contain NULL and DEFAULT values, but cannot contain:

-   LOB \(BLOB or CLOB\) columns
-   BINARY, or VARBINARY columns
-   CHAR or VARCHAR columns whose length is over 255 bytes
-   BIT columns
-   FLOAT/DOUBLE/REAL columns


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
range-partition-decl:
  <partition-name> VALUES <= ( {<constant-expression> |  MAX } ) 
;
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

    In addition, partition bound values must be compatible with the corresponding partition-key column data type. For example, VARCHAR is compatible with CHAR.

-   If a bound value has a different data type than that of its corresponding partition key column, data lake Relational Engine converts the bound value to the data type of the partition key column, with these exceptions:

    -   Explicit conversions are not allowed. This example attempts an explicit conversion from INT to VARCHAR and generates an error:

        ```
        CREATE TABLE Employees(emp_name VARCHAR(20)) 
        PARTITION BY RANGE(emp_name)
        (p1 VALUES <=(CAST (1 AS VARCHAR(20))), 
        p2 VALUES <= (CAST (10 AS VARCHAR(20)));
        ```

    -   Implicit conversions that result in data loss are not allowed. In this example, the partition bounds are not compatible with the partition key type. Rounding assumptions may lead to data loss and an error is generated:

        ```
        CREATE TABLE emp_id (id INT) PARTITION BY RANGE(id) (p1 VALUES <= (10.5), p2 VALUES <= (100.5));
        ```


-   In this example, the partition bounds and the partition key data type are compatible. The bound values are directly converted to float values. No rounding is required, and conversion is supported:

    ```
    CREATE TABLE id_emp (id FLOAT)
    PARTITION BY RANGE(id) (p1 VALUES <= (10), 
    p2 VALUES <= (100));
    ```

-   Conversions from non-binary data types to binary data types are not allowed. For example, this conversion is not allowed and returns an error:

    ```
    CREATE TABLE newemp (name BINARY)
    PARTITION BY RANGE(name) 
    (p1 VALUES <= ('Maarten'), 
    p2 VALUES <= ('Zymmerman');
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
   PARTITION BY HASH  ( <column_name> [,... ] );
    SUBPARTITION BY <range-partition-scheme>;
```

The hash partition specifies how the data is logically distributed and colocated; the range subpartition specifies how the data is physically placed. The new range subpartition is logically partitioned by hash with the same hash partition keys as the existing hash-range partitioned table. The range subpartition key is restricted to one column.

Restrictions:

-   You can only hash partition a base table. Attempting to partition a global temporary table or a local temporary table raises an error.
-   You cannot add, drop, merge, or split a hash partition.
-   You cannot add or drop a column from a hash partition key.



</dd>
</dl>



</dd>
</dl>



<a name="loioa619764084f21015b8039a8346dc622c__create_table_remarks1"/>

## Remarks

You can create a table for another user by specifying an owner name. If GLOBAL TEMPORARY or LOCAL TEMPORARY is not specified, the table is referred to as a base table. Otherwise, the table is a temporary table.

A created global temporary table exists in the database like a base table and remains in the database until it is explicitly removed by a DROP TABLE statement. The rows in a temporary table are visible only to the connection that inserted the rows. Multiple connections from the same or different applications can use the same temporary table at the same time and each connection sees only its own rows. A given connection inherits the schema of a global temporary table as it exists when the connection first refers to the table. The rows of a temporary table are deleted when the connection ends.

When you create a local temporary table, omit the owner specification. If you specify an owner when creating a temporary table, for example, CREATE TABLE \#temp\(col1 int\), a base table is incorrectly created.

An attempt to create a base table or a global temporary table will fail, if a local temporary table of the same name exists on that connection, as the new table cannot be uniquely identified by owner.table.

You can, however, create a local temporary table with the same name as an existing base table or global temporary table. References to the table name access the local temporary table, as local temporary tables are resolved first.

For example, consider this sequence:

```
CREATE TABLE t1 (c1 int);
INSERT t1 VALUES (9);

CREATE LOCAL TEMPORARY TABLE t1 (c1 int);
INSERT t1 VALUES (8);

SELECT * FROM t1;
```

The result returned is 8. Any reference to t1 refers to the local temporary table t1 until the local temporary table is dropped by the connection.

In a procedure, use the CREATE LOCAL TEMPORARY TABLE statement, instead of the DECLARE LOCAL TEMPORARY TABLE statement, when you want to create a table that persists after the procedure completes. Local temporary tables created using the CREATE LOCAL TEMPORARY TABLE statement remain until they are either explicitly dropped, or until the connection closes.

Local temporary tables created in IF statements using CREATE LOCAL TEMPORARY TABLE also persist after the IF statement completes.

Data lake Relational Engine does not support the CREATE TABLE ENCRYPTED clause for table-level encryption of data lake Relational Engine tables. However, the CREATE TABLE ENCRYPTED clause is supported for SAP SQL Anywhere tables in a data lake Relational Engine database.



<a name="loioa619764084f21015b8039a8346dc622c__create_table_privileges1"/>

## Privileges



### 

The privileges required depend on type of table being created.


<table>
<tr>
<th valign="top">

Table Type

</th>
<th valign="top">

Privileges Required

</th>
</tr>
<tr>
<td valign="top">

Base table and global temporary table

</td>
<td valign="top">

-   To create a self-owned base or temporary table requires one of:
    -   CREATE TABLE system privilege

-   To create a base or temporary table owned by another user, requires one of:
    -   CREATE ANY TABLE system privilege
    -   CREATE ANY OBJECT system privilege
    -   CREATE ANY object-level privilege on the schema to contain the table if the schema is owned by another user.




</td>
</tr>
<tr>
<td valign="top">

Proxy table

</td>
<td valign="top">

-   To create a self owned proxy table requires one of:
    -   CREATE PROXY TABLE system privilege

-   To create a proxy table owned by another user requires one of:
    -   CREATE ANY TABLE system privilege
    -   CREATE ANY OBJECT system privilege
    -   CREATE ANY object-level privilege on the schema containing the table if the schema is owned by another user.




</td>
</tr>
<tr>
<td valign="top">

FOREIGN KEY

</td>
<td valign="top">

In addition to the specified privileges required to create the table, to include a FOREIGN KEY you also require one of:

-   You own the table.
-   INDEX ANY TABLE system privilege
-   REFERENCES object-level privilege on the table.
-   CREATE ANY or REFERENCES object-level privilege on the schema if the schema is owned by another user.



</td>
</tr>
</table>

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) or [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md) for assistance with granting privileges. 



<a name="loioa619764084f21015b8039a8346dc622c__create_table_side_effects1"/>

## Side Effects

Automatic commit



<a name="loioa619764084f21015b8039a8346dc622c__create_table_standards1"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar. Vendor extensions are:
    -   The \{ IN | ON \} *<dbspace-name\>* clause
    -   The ON COMMIT clause
    -   Some of the default values




<a name="loioa619764084f21015b8039a8346dc622c__create_table_examples1"/>

## Examples

-   This example creates a table T1 with three partitions:

    ```
    CREATE TABLE T1 (C1 INT, C2 INT)
       PARTITION BY RANGE(C1) (P1 VALUES <= (0), P2 VALUES <= (10), P3 VALUES <= (100));
    ```

-   This example creates a HASH partitioned \(table TBL42\) that includes a PRIMARY KEY \(column C1\) and a HASH PARTITION KEY \(columns C4 and C3\):

    ```
    CREATE TABLE TBL42 (
        C1 BIGINT NOT NULL,
        C2 VARCHAR(2) IQ UNIQUE(50),
        C3 DATE IQ UNIQUE(36524),
        C4 VARCHAR(200),
      PRIMARY KEY (C1)) 
      PARTITION BY HASH (C4, C3);
    ```

-   This example creates a table for a library database to hold information on borrowed books:

    ```
    CREATE TABLE BORROWED_BOOK (
       DATE_BORROWED DATE NOT NULL, 
       DATE_RETURNED DATE,
       BOOK_NAME VARCHAR(20)
      REFERENCES LIBRARY_BOOKS (isbn), CHECK( DATE_RETUREND >= DATE_BORROWED ));
    ```


**Related Information**  


[ALTER TABLE Statement for Data Lake Relational Engine](alter-table-statement-for-data-lake-relational-engine-39f1ec0.md "Modifies a table definition.")

[DROP TABLE Statement for Data Lake Relational Engine](drop-table-statement-for-data-lake-relational-engine-0524ea8.md "Removes a table from the database.")

[CREATE INDEX Statement for Data Lake Relational Engine](create-index-statement-for-data-lake-relational-engine-a617ca4.md "Creates an index on a specified table, or pair of tables. Once an index is created, it is never referenced in a SQL statement again except to delete it using the DROP INDEX statement.")

[SQL Data Types in Data Lake Relational Engine](../020-sql-data-types/sql-data-types-in-data-lake-relational-engine-2fe779f.md "SQL data types define the type of data to be stored, such as character strings, numbers, and dates.")

[ALLOW\_NULLS\_BY\_DEFAULT Option \[TSQL\] for Data Lake Relational Engine](../090-database-options/allow-nulls-by-default-option-tsql-for-data-lake-relational-engine-a62c2ca.md "Controls whether new columns created without specifying either NULL or NOT NULL are allowed to contain NULL values.")

[DECLARE LOCAL TEMPORARY TABLE Statement for Data Lake Relational Engine](declare-local-temporary-table-statement-for-data-lake-relational-engine-a61b247.md "Declares a local temporary table.")

[FP\_NBIT\_AUTOSIZE\_LIMIT Option for Data Lake Relational Engine](../090-database-options/fp-nbit-autosize-limit-option-for-data-lake-relational-engine-a873755.md "Limits the number of distinct values in columns that implicitly load as NBit FP.")

[FP\_NBIT\_ENFORCE\_LIMITS Option for Data Lake Relational Engine](../090-database-options/fp-nbit-enforce-limits-option-for-data-lake-relational-engine-a874045.md "Enforces sizing limits for explicit and implicit NBit columns.")

[FP\_NBIT\_LOOKUP\_MB Option for Data Lake Relational Engine](../090-database-options/fp-nbit-lookup-mb-option-for-data-lake-relational-engine-a873a52.md "Limits the total dictionary size per column for implicit NBit FP columns.")

[FP\_NBIT\_ROLLOVER\_MAX\_MB Option for Data Lake Relational Engine](../090-database-options/fp-nbit-rollover-max-mb-option-for-data-lake-relational-engine-a873d4b.md "Sets a threshold for the total dictionary size for implicit NBit rollovers to Flat FP.")

[IDENTITY\_INSERT Option for Data Lake Relational Engine](../090-database-options/identity-insert-option-for-data-lake-relational-engine-a63914e.md "Enables users to insert values into or to update an IDENTITY or AUTOINCREMENT column.")

[Restrictions on Table Partitions](https://help.sap.com/viewer/a8937bea84f21015a80bc776cf758d50/2023_4_QRC/en-US/a872506a84f21015aa20de6d7665a803.html "Some restrictions apply to table partitions.") :arrow_upper_right:

[Hash-Range Partitions](https://help.sap.com/viewer/a8937bea84f21015a80bc776cf758d50/2023_4_QRC/en-US/a871ecd884f21015b8f5876892d31447.html "Hash-range partitioning is a composite partitioning scheme that subpartitions a hash-partitioned table by range.") :arrow_upper_right:

[Hash Partitions](https://help.sap.com/viewer/a8937bea84f21015a80bc776cf758d50/2023_4_QRC/en-US/a871bc0984f210159faaedf3f3eb5b29.html "Hash partitioning maps data to partitions based on partition-key values processed by an internal hashing function.") :arrow_upper_right:

[Range Partitions](https://help.sap.com/viewer/a8937bea84f21015a80bc776cf758d50/2023_4_QRC/en-US/a8721b7584f21015a062c99a1c19e6cb.html "Range partitioning divides large tables by a range of partition-key values established for each partition.") :arrow_upper_right:

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[CREATE TABLE Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/6c3afae6093f4327a6aa7fb91c1caafe.html "Creates a new table in the database or on a remote server.") :arrow_upper_right:

