<!-- loioa61b247c84f2101584efe462c353b5a0 -->

# DECLARE LOCAL TEMPORARY TABLE Statement for Data Lake Relational Engine

Declares a local temporary table.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
DECLARE LOCAL TEMPORARY TABLE <table-name>
   … ( <column-definition> [ <column-constraint> ] …
   [ , <column-definition> [ <column-constraint> ] … ]
   [ , <table-constraint> ] … )
   …[ ON COMMIT { DELETE | PRESERVE } ROWS ]
```



<a name="loioa61b247c84f2101584efe462c353b5a0__IQ_Usage"/>

## Remarks

`DECLARE LOCAL TEMPORARY TABLE` declares a temporary table.

A local temporary table and the rows in it are visible only to the connection that created the table and inserted the rows. By default, the rows of a temporary table are deleted on `COMMIT`.

Declared local temporary tables within compound statements exist within the compound statement. Otherwise, the declared local temporary table exists until the end of the connection.

See *CREATE TABLE Statement* for definitions of *<column-definition\>*, *<column-constraint\>*, and *<table-constraint\>* syntax. See *SELECT Statement* for an example of how to select data into a temporary table.

Once you create a local temporary table, either implicitly or explicitly, you cannot create another temporary table of that name for as long as the temporary table exists. For example, you can create a local temporary table implicitly:

```
select * into #tmp from table1
```

Alternatively, you can create a local temporary table with an explicit by declaration:

```
declare local temporary table foo
```

Then if you try to select into `#tmp` or `foo`, or declare `#tmp` or `foo` again, you receive an error indicating that `#tmp` or `foo` already exists.

When you declare a local temporary table, omit the owner specification. If you specify the same `owner.table` in more than one `DECLARE LOCAL TEMPORARY TABLE` statement in the same session, a syntax error is reported. For example, an error is reported when these statements are executed in the same session:

```
DECLARE LOCAL TEMPORARY TABLE user1.temp(col1 int);
DECLARE LOCAL TEMPORARY TABLE user1.temp(col1 int);
```

If the owner name is omitted, then the error ***Item temp already exists*** is reported:

```
DECLARE LOCAL TEMPORARY TABLE temp(col1 int);
DECLARE LOCAL TEMPORARY TABLE temp(col1 int);
```

An attempt to create a base table or a global temporary table fails, if a local temporary table of the same name exists on that connection, as the new table cannot be uniquely identified by *<owner.table\>*.

You can, however, create a local temporary table with the same name as an existing base table or global temporary table. References to the table name access the local temporary table, as local temporary tables are resolved first.

For example, consider this sequence:

```
CREATE TABLE t1 (c1 int);
INSERT t1 VALUES (9);

DECLARE LOCAL TEMPORARY TABLE t1 (c1 int);
INSERT t1 VALUES (8);

SELECT * FROM t1;
```

The result returned is 8. Any reference to `t1` refers to the local temporary table `t1` until the local temporary table is dropped by the connection.

You cannot use the following on local temporary tables:

-   Statements – `ALTER TABLE`, `DROP INDEX`.
-   Stored procedures – `sp_iqindex`, `sp_iqtablesize`, and `sp_iqindexsize`.



<a name="loioa61b247c84f2101584efe462c353b5a0__IQ_Permissions"/>

## Privileges

None



<a name="loioa61b247c84f2101584efe462c353b5a0__IQ_Standards"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loioa61b247c84f2101584efe462c353b5a0__IQ_Examples"/>

## Examples

-   The following example declares a local temporary table in Embedded SQL:

    ```
    EXEC SQL DECLARE LOCAL TEMPORARY TABLE MyTable (
      number INT
      );
    ```

-   The following example declares a local temporary table in a stored procedure:

    ```
    BEGIN
      DECLARE LOCAL TEMPORARY TABLE TempTab (
        number INT
      );
      ...
    END
    ```


**Related Information**  


[CREATE TABLE Statement for Data Lake Relational Engine](create-table-statement-for-data-lake-relational-engine-a619764.md "Creates a new table in the database or on a remote server.")

[SELECT Statement for Data Lake Relational Engine](select-statement-for-data-lake-relational-engine-a624e72.md "Retrieves information from the database.")

