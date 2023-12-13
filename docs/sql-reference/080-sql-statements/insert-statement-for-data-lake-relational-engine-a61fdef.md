<!-- loioa61fdeff84f21015aa66b9add387d7f9 -->

# INSERT Statement for Data Lake Relational Engine

Inserts a single row or a selection of rows, from elsewhere in the current database, into the table. This command can also insert a selection of rows from another database into the table.



<a name="loioa61fdeff84f21015aa66b9add387d7f9__section_azh_5fj_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.




<dl>
<dt><b>

Syntax 1

</b></dt>
<dd>

```
INSERT [ INTO ] [ { <owner> | <schema-name> }.]<table-name> 
   [ ( <column-name> [, …] ) ] VALUES [ ( { <expression> | DEFAULT }[, ...] ) ];
```



</dd><dt><b>

Syntax 1a

</b></dt>
<dd>

```
INSERT [ INTO ] [ { <owner> | <schema-name> }.]<table-name> 
   DEFAULT VALUES;
```



</dd><dt><b>

Syntax 2

</b></dt>
<dd>

```
INSERT [ INTO ] [ { <owner> | <schema-name> }.]<table-name> [ ( <column-name> [, …] ) ]
   ... <insert-load-options> <insert-select-load-options>
   ... <select-statement>;
```



</dd><dt><b>

Syntax 3

</b></dt>
<dd>

```
INSERT [ INTO ] [ { <owner> | <schema-name> }.]<table-name>[ ( <column-name> [, …] ) ]
    ... <insert-select-load-options> <insert-select-load-options>
    ... LOCATION '<servername.dbname>' [ <location-options> ]
   ... { <select-statement> | '<select statement>' };
```



</dd>
</dl>

```
<insert-load-options> ::=
   [ LIMIT <number-of-rows> ] 
   [ NOTIFY <number-of-rows> ] 
   [ SKIP <number-of-rows> ];
```

```
<insert-select-load-options> ::=
   [ WORD SKIP <number> ]
   [ IGNORE CONSTRAINT <constraint-type> [, …] ] 
   [ MESSAGE LOG '<string>' ROW LOG '<string>' [ ONLY LOG <logwhat> [, …] ] ] 
   [ LOG DELIMITED BY '<string>' ];
```

```
<location-options> ::=
   { PACKETSIZE <interger>
   | QUOTED_IDENTIFIER { ON | OFF }
   | ISOLATION LEVEL <integer> };
```

```
<constraint-type> ::=
   { CHECK <integer> 
   | UNIQUE <integer> 
   | NULL <integer> 
   | FOREIGN KEY <integer> 
   | DATA VALUE <integer> 
   | ALL <integer> };
```

```
<logwhat> ::=
   { CHECK 
   | ALL 
   | NULL
   | UNIQUE
   | DATA VALUE
   | FOREIGN KEY
   | WORD };
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa61fdeff84f21015aa66b9add387d7f9__insert_parameters1"/>

## Parameters


<dl>
<dt><b>

*<insert-load-options\>*

</b></dt>
<dd>

Options that constrain the load:

-   LIMIT – specifies the maximum number of rows to insert into the table from a query. The default is 0 for no limit. The maximum is 2 GB -1.
-   NOTIFY – specifies that you be notified with a message each time the number of rows are successfully inserted into the table. The default is every 100,000 rows.
-   SKIP – defines the number of rows to skip at the beginning of the input tables for this insert. The default is 0.



</dd><dt><b>

*<insert-select-load-options\>*

</b></dt>
<dd>


<dl>
<dt><b>

WORD SKIP

</b></dt>
<dd>

Allows the load to continue when it encounters data longer than the limit specified when the word index was created. The *<number\>* parameter specifies the number of times to ignore the error. Setting this option to 0 means there is no limit.

If a row is not loaded because a word exceeds the maximum permitted size, a warning is written to the `.iqmsg` file. WORD size violations can be optionally logged to the MESSAGE LOG file. If the option is not specified, the operation rolls back on the first occurrence of a word that is longer than the specified limit.



</dd><dt><b>

IGNORE CONSTRAINT

</b></dt>
<dd>

Determines whether the load engine ignores CHECK, UNIQUE, NULL, DATA VALUE, and FOREIGN KEY integrity constraint violations that occur during a load and the maximum number of violations to ignore before initiating a rollback.

If *<limit\>* is zero, the number of CHECK constraint violations to ignore is infinite. If CHECK is not specified, the first occurrence of any CHECK constraint violation causes the load to roll back. If *<limit\>* is nonzero, then the *<limit\>* +1 occurrence of a CHECK constraint violation causes the load to roll back



</dd><dt><b>

MESSAGE LOG

</b></dt>
<dd>

Specifies the file names where the load engine logs integrity constraint violations. Timestamps indicating the start and completion of the load are logged in both the MESSAGE LOG and the ROW LOG files. Both MESSAGE LOG and ROW LOG must be specified, or no information about integrity violations is logged.

Information is logged on all integrity constraint-type violations specified in the ONLY LOG clause or for all word index-length violations if the keyword WORD is specified. If the ONLY LOG clause is not specified, no information on integrity constraint violations is logged. Only the timestamps indicating the start and completion of the load are logged.



</dd><dt><b>

LOG DELIMITED BY

</b></dt>
<dd>

Specifies the separator between data values in the ROW LOG file. The default separator is a comma.



</dd>
</dl>



</dd><dt><b>

*<location-options\>*

</b></dt>
<dd>


<dl>
<dt><b>

PACKETSIZE

</b></dt>
<dd>

Specifies the TDS packet-size in bytes. The default TDS packet-size on most platforms is 512 bytes. If the packet size is not specified or is specified as zero, then the default packet size value for the platform is used.

The packet-size value must be a multiple of 512, either equal to the default network packet size or between the default network packet size and the maximum network packet size. The maximum network packet size and the default network packet size are multiples of 512 in the range 512 – 524288 bytes. The maximum network packet size is always greater than or equal to the default network packet size.



</dd><dt><b>

QUOTED\_IDENTIFIER

</b></dt>
<dd>

Sets the QUOTED\_IDENTIFIER option on the remote server. The default setting is OFF. You set QUOTED\_IDENTIFIER to ON only if any of the identifiers in the SELECT statement are enclosed in double quotes, as in this example using "c1":

```
INSERT INTO foo
LOCATION 'ase.database'
QUOTED_IDENTIFIER ON {select "c1" from xxx}; 
```



</dd><dt><b>

ISOLATION LEVEL

</b></dt>
<dd>

Specifies an isolation level for the connection to a remote server. The levels and their characteristics are:

-   READ UNCOMMITTED

    -   Isolation level 0
    -   Read permitted on row with or without write lock
    -   No read locks are applied
    -   No guarantee that concurrent transaction will not modify row or roll back changes to row

-   READ COMMITTED

    -   Isolation level 1
    -   Read only permitted on row with no write lock
    -   Read lock acquired and held for read on current row only, but released when cursor moves off the row
    -   No guarantee that data will not change during transaction

-   SERIALIZABLE

    -   Isolation level 3
    -   Read only permitted on rows in result without write lock
    -   Read locks acquired when cursor is opened and held until transaction ends




</dd>
</dl>



</dd>
</dl>



<a name="loioa61fdeff84f21015aa66b9add387d7f9__insert_remarks1"/>

## Remarks

Syntax 1 and 1a allows the insertion of a single row with the specified expression values. If the list of column names is not specified, the values are inserted into the table columns in the order they were created \(the same order as retrieved with SELECT \*\). The row is inserted into the table at an arbitrary position. \(In relational databases, tables are not ordered.\)

Syntax 2 allows the user to perform a mass insertion into a table using the results of a fully general SELECT statement. Insertions are done in an arbitrary order unless the SELECT statement contains an ORDER BY clause. The columns from the select list are matched ordinally with the columns specified in the column list, or sequentially in the order in which the columns were created.

> ### Note:  
> The NUMBER\(\*\) function is useful for generating primary keys with Syntax 2 of the INSERT statement.

Syntax 3 INSERT...LOCATION is a variation of Syntax 2 that allows you to insert data from an SAP Adaptive Server Enterprisedata lake Relational Engine or data lake Relational Engine database. The *<servername.dbname\>* specified in the LOCATION clause identifies the remote server and database for the table in the FROM clause.

The external login is defined on the IQ server as:

```
CREATE EXTERNLOGIN russid TO ase1 REMOTE LOGIN ase1user IDENTIFIED BY mydatabase;
```

Character strings inserted into tables are always stored in the case they are entered, regardless of whether the database is case-sensitive or not. Thus, a string “Value” inserted into a table is always held in the database with an uppercase V and the remainder of the letters lowercase. SELECT statements return the string as 'Value.' If the database is not case-sensitive, however, all comparisons make 'Value' the same as 'value,' 'VALUE," and so on. Further, if a single-column primary key already contains an entry Value, an INSERT of value is rejected, as it would make the primary key not unique.

Whenever you execute an INSERT...LOCATION statement, data lake Relational Engine loads the localization information needed to determine language, collation sequence, character set, and date/time format.

Use the \(DEFAULT\), DEFAULT VALUES or VALUES\(\) clauses to insert rows with all default values. Assuming that there are 3 columns in table t2, these examples are semantically equivalent:

```
INSERT INTO t2 values (DEFAULT, DEFAULT, DEFAULT);
```

```
INSERT INTO t2 DEFAULT VALUES;
```

```
INSERT INTO t2() VALUES();
```

INSERT...VALUES also supports multiple rows. The following example inserts 3 rows into table t1:

```
CREATE TABLE t1(c1 varchar(30));
INSERT INTO t1 VALUES  ('morning'),('afternoon'),
    ('evening');
```

Data lake Relational Engine treats all load/inserts as full-width inserts. Columns not explicitly specified on the load/insert statement, the value loaded will either be the column’s DEFAULT value \(if one is defined\) or NULL \(if no DEFAULT value is defined for the column\).

Data lake Relational Engine supports column DEFAULT values for INSERT...VALUES, INSERT...SELECT, and INSERT...LOCATION. If a DEFAULT value is specified for a column, this DEFAULT value is used as the value of the column in any INSERT \(or LOAD\) statement that does not specify a value for the column.

An INSERT from a stored procedure or function is not permitted, if the procedure or function uses COMMIT, ROLLBACK, or some ROLLBACK TO SAVEPOINT statements.

The result of a SELECT…FROM may be slightly different from the result of an INSERT…SELECT…FROM due to an internal data conversion of an imprecise data type, such as DOUBLE or NUMERIC, for optimization during the insert. If a more precise result is required, a possible workaround is to declare the column as a DOUBLE or NUMERIC data type with a higher precision.



<a name="loioa61fdeff84f21015aa66b9add387d7f9__insert_privileges1"/>

## Privileges



### 

To INSERT into tables and views requires one of:

-   You own the object
-   INSERT ANY TABLE system privilege
-   INSERT object-level privilege on the object
-   INSERT object-level privilege on the schema containing the object if the schema is owned by another user.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) or [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md) for assistance with granting privileges.



<a name="loioa61fdeff84f21015aa66b9add387d7f9__insert_standards1"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products – supported by SAP Adaptive Server Enterprise \(excluding the *<insert-load-options\>*\).



<a name="loioa61fdeff84f21015aa66b9add387d7f9__insert_examples1"/>

## Examples

-   The following example adds an Eastern Sales department to the database:

    ```
    INSERT INTO Departments
    (DepartmentID, DepartmentName, DepartmentHeadID)
    VALUES (600, 'Eastern Sales', 501);
    ```

-   The following example fills the table dept\_head with the names of department heads and their departments:

    ```
    INSERT INTO dept_head (name, dept)
      NOTIFY 20
      SELECT Surname || ' ' || GivenName
      AS name,
      dept_name
    FROM Employees JOIN Departments
      ON EmployeeID= DepartmentHeadID;
    ```

-   The following example inserts data from the l\_shipdate and l\_orderkey columns of the lineitem table from the data lake Relational Engine database iqdet on the remote server detroit into the corresponding columns of the lineitem table in the current database:

    ```
    INSERT INTO lineitem
      (l_shipdate, l_orderkey)
      LOCATION 'detroit.iqdet'
      PACKETSIZE 512
      ' SELECT l_shipdate, l_orderkey
    FROM lineitem ';
    ```

-   The INSERT statement permits a list of values allowing several rows to be inserted at once:

    ```
    INSERT into t1 values( 10, 20, 30 ), ( 11, 21, 31 ), ( 12, 22, 32 );
    ```


**Related Information**  


[LOAD TABLE Statement \(Non-Parquet Formats\) for Data Lake Relational Engine](load-table-statement-non-parquet-formats-for-data-lake-relational-engine-7ca3f60.md "Imports data into a data lake Relational Engine database table from either the external object store (Azure BLOB storage, an Amazon S3 bucket, an S3-compliant bucket, or Google Cloud Storage) or from data lake Files containers (the managed object store).")

[INSERT Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/cbe6857cc94b4923a6ee5917651f5084.html "Inserts a single row or a selection of rows, from elsewhere in the current database, into the table. This command can also insert a selection of rows from another database into the table.") :arrow_upper_right:

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[REVOKE Object-Level Privilege Statement for Data Lake Relational Engine](revoke-object-level-privilege-statement-for-data-lake-relational-engine-a3e7af2.md "Removes object-level privileges that were given using the GRANT statement.")

