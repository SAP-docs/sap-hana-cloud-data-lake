<!-- loioa617ca4484f21015b2cdfdebbf4a5eee -->

# CREATE INDEX Statement for Data Lake Relational Engine 

Creates an index on a specified table, or pair of tables. Once an index is created, it is never referenced in a SQL statement again except to delete it using the DROP INDEX statement.



<a name="loioa617ca4484f21015b2cdfdebbf4a5eee__section_azh_5fj_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
CREATE [ UNIQUE ] [ <index-type> ] INDEX [ IF NOT EXISTS ] <index-name>
   … ON [ { <owner> | <schema-name> }.]<table-name>
   … ( <column-name> [ , <column-name> ] … )
   … [ NOTIFY <integer> ]
   … [ DELIMITED BY '<separators-string>' ]
   … [ LIMIT <maxwordsize-integer> ]
```

```
<index-type> ::=
   { CMP | DATE | DTTM | HG | HNG | TIME | WD }
```

> ### Tip:  
> Looking for TEXT index information? See [CREATE TEXT INDEX Statement for Data Lake Relational Engine](create-text-index-statement-for-data-lake-relational-engine-a602ced.md).



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa617ca4484f21015b2cdfdebbf4a5eee__create_index_parameters1"/>

## Parameters


<dl>
<dt><b>

*<index-type\>*

</b></dt>
<dd>

For columns in data lake Relational Engine tables, you can specify an *<index-type\>* of the following:

-   CMP
-   DATE
-   DTTM – Datetime
-   HG – High\_Group \(default\)
-   HNG
-   TIME
-   WD – Word

> ### Tip:  
> Looking for TEXT index information? See [CREATE TEXT INDEX Statement for Data Lake Relational Engine](create-text-index-statement-for-data-lake-relational-engine-a602ced.md).

If you do not specify an *<index-type\>*, an HG index is created by default.

To create an index on the relationship between two columns in an IQ main store table, you can specify an *<index-type\>* of CMP \(Compare\). Columns must be of identical data type, precision and scale. For a CHAR, VARCHAR, BINARY or VARBINARY column, precision means that both columns have the same width.

For maximum query speed, the correct type of index for a column depends on:

-   The number of unique values in the column
-   How the column is going to be used in queries
-   The amount of storage space available

You can specify multiple indexes on a column of an IQ main store table, but these must be of different index types. CREATE INDEX does not let you add a duplicate index type. Data lake Relational Engine chooses the fastest index available for the current query or portion of the query. However, each additional index type might significantly add to the space requirements of that table.



</dd><dt><b>

*<column-name\>*

</b></dt>
<dd>

Specifies the name of the column to be indexed. A column name is an identifier preceded by an optional correlation name. \(A correlation name is usually a table name. For more information on correlation names, see *FROM Clause*.\) If a column name has characters other than letters, digits, and underscore, enclose it in quotation marks \(“”\).

Only the HG and CMP index types can be specified on a multi-column index.

Foreign keys require nonunique indexes and composite foreign keys require nonunique composite HG indexes. CHAR, VARCHAR, BINARY, and VARBINARY data cannot be more than 5300 bytes in a single-column HG index. A multi-column HG index \(both unique and non-unique\) can contain a single CHAR, VARCHAR, or BINARY column of up to 5297 bytes.



</dd><dt><b>

UNIQUE

</b></dt>
<dd>

Permitted for index type HG only. Ensures that no two rows in the table have identical values in all the columns in the index. Each index key must be unique or contain a NULL in at least one column.

Data lake Relational Engine allows the use of NULL in data values on a user created unique multicolumn HG index, if the column definition allows for NULL values and a constraint \(primary key or unique\) is not being enforced.



</dd><dt><b>

IF NOT EXISTS

</b></dt>
<dd>

If the named object already exists, no changes are made and an error is not returned.



</dd><dt><b>

DELIMITED BY

</b></dt>
<dd>

Specifies separators to use in parsing a column string into the words to be stored in the WD index of that column. If you omit this clause or specify the value as an empty string, data lake Relational Engine uses the default set of separators. The default set of separators is designed for the default collation order \(ISO-BINENG\). It includes all 7-bit ASCII characters that are not 7-bit ASCII alphanumeric characters, except for the hyphen and the single quotation mark. The hyphen and the single quotation mark are part of words by default. There are 64 separators in the default separator set. For example, if the column value is this string:

```
The cat is on the mat
```

and the database was created with the CASE IGNORE setting using default separators, these words are stored in the WD index from this string:

```
cat is mat on the
```

If you specify multiple DELIMITED BY and LIMIT clauses, no error is returned, but only the last clause of each type is used.



</dd><dt><b>

*<separators-string\>*

</b></dt>
<dd>

Must be a sequence of 0 or more characters in the collation order used when the database was created. Each character in the separators string is treated as a separator. If there are no characters in the separators string, the default set of separators is used. \(Each separator must be a single character in the collation sequence being used.\) There cannot be more than 256 characters \(separators\) in the separators string.

To specify tab as a delimiter, you can either type a [TAB\] character within the separator string, or use the hexadecimal ASCII code of the tab character, \\x09. “\\t” specifies two separators, \\ and the letter t. To specify newline as a delimiter, you can type a [RETURN\] character or the hexadecimal ASCII code \\x0a.

For example, the clause DELIMITED BY ' :;.\\/t' specifies these seven separators: space : ; . \\ / t


<table>
<tr>
<th valign="top">

Delimiter

</th>
<th valign="top">

Separator String for the DELIMITED BY Clause

</th>
</tr>
<tr>
<td valign="top">

tab

</td>
<td valign="top">

Either of the following:

-   ' ' \(type [TAB\]\)
-   '\\x09'



</td>
</tr>
<tr>
<td valign="top">

newline

</td>
<td valign="top">

Either of the following:

-   ' ' \(type [RETURN\]\)
-   '\\x0a'



</td>
</tr>
</table>



</dd><dt><b>

LIMIT

</b></dt>
<dd>

Can be used for the creation of the WD index only. Specifies the maximum word length that is permitted in the WD index. Longer words found during parsing causes an error. The default is 255 bytes. The minimum permitted value is 1 and the maximum permitted value is 255. If the maximum word length specified in the CREATE INDEX statement or determined by default exceeds the column width, the used maximum word length is silently reduced to the column width. Using a lower maximum permitted word length allows insertions, deletions, and updates to use less space and time. The empty word \(two adjacent separators\) is silently ignored. After a WD index is created, any insertions into its column are parsed using the separators and maximum word size determined at create time. These separators and maximum word size cannot be changed after the index is created.



</dd><dt><b>

NOTIFY

</b></dt>
<dd>

Gives notification messages after n records are successfully added for the index. The messages are sent to the standard output device. A message contains information about memory usage, database space, and how many buffers are in use. The default is 100,000 records. To turn off NOTIFY, set it to 0.



</dd>
</dl>



<a name="loioa617ca4484f21015b2cdfdebbf4a5eee__create_index_remarks1"/>

## Remarks

-   There is no way to specify the index owner in the CREATE INDEX statement. Indexes are automatically owned by the owner of the table on which they are defined. The index name must be unique for each owner.

-   Indexes cannot be created for views. The name of each index must be unique for a given table.

-   CREATE INDEX is prevented whenever the statement affects a table currently being modified by another connection. However, queries are allowed on a table that is also adding an index.

-   After a WD index is created, any insertions into its column are parsed using the separators, and maximum word size cannot be changed after the index is created. For CHAR columns, specify a space as at least one of the separators or use the default separator set. Data lake Relational Engine automatically pads CHAR columns to the maximum column width. If your column contains blanks in addition to the character data, queries on WD indexed data might return misleading results. For example, column CompanyName contains two words delimited by a separator, but the second word is blank padded:

    ```
    'Concord' 'Farms       '
    ```

    Suppose that a user entered this query:

    ```
    SELECT COUNT(*)FROM Customers WHERE CompanyName contains ('Farms');
    ```

    The parser determines that the string contains the following, instead of 'Farms', and returns 0 instead of 1:

    ```
    'Farms           '
    ```

    You can avoid this problem by using VARCHAR instead of CHAR columns.

-   Data types:

    -   You cannot use CREATE INDEX to create an index on a column with BIT data.
    -   Only the default index, CMP index, or WD index can be created on CHAR and VARCHAR data with more than 255 bytes.
    -   Only the default and WD index types can be created on LONG VARCHAR data.
    -   Only the default index, CMP index, and TEXT index types can be created on BINARY and VARBINARY data with more than 255 bytes.
    -   A CMP index cannot be created on a column with FLOAT, REAL, or DOUBLE data.
    -   A TIME index can be created only on a column having the data type TIME.
    -   A DATE index can be created only on a column having the data type DATE.
    -   A DTTM index can be created only on a column having the data type DATETIME or TIMESTAMP.

-   You can create a unique or nonunique HG index with more than one column. Data lake Relational Engine implicitly creates a nonunique HG index on a set of columns that makes up a foreign key.

    HG and CMP are the only types of indexes that can have multiple columns. You cannot create a DATE, TIME, or index with more than one column.

    The maximum width of a multicolumn concatenated key is 5 KB \(5300 bytes\). The number of columns allowed depends on how many columns can fit into 5 KB. CHAR or VARCHAR data greater than 255 bytes are not allowed as part of a composite key in single-column HG, DATE, TIME, or DTTM indexes.

    An INSERT on a multicolumn index must include all columns of the index.

    Queries with a single column in the ORDER BY clause run faster using multicolumn HG indexes. In the following example the HG index vertically projects *<x\>* in sorted order:

    ```
    SELECT abs (x) from t1
    ORDER BY x;
    ```

    To enhance query performance, use multicolumn HG indexes to run ORDER BY operations on more than one column \(that can also include ROWID\) in the SELECT or ORDER BY clause with these conditions:

    -   All projected columns, plus all ordering columns \(except ROWID\), exist within the index
    -   The ordering keys match the leading `` columns, in order

    If more than one multicolumn HG index with the lowest distinct counts is used. index satisfies these conditions, the index with the lowest distinct counts is used. If a query has an ORDER BY clause, and the ORDER BY column list is a prefix of a multicolumn index where all columns referenced in the If a query has an ORDER BY clause, and the ORDER BY column list is a prefix of a multicolumn index where all columns referenced in the index with the lowest distinct counts is used. index satisfies these conditions, the index with the lowest distinct counts is used.If a query has an ORDER BY clause, and the ORDER BY column list is a prefix of a multicolumn index where all columns referenced in the If a query has an ORDER BY clause, and the ORDER BY column list is a prefix of a multicolumn index where all columns referenced in the SELECT list are present in a multicolumn index, then the multicolumn index performs vertical projection; for example:

    ```
    SELECT x,z,y FROM T 
    ORDER BY x,y;
    ```

    If expressions exist on base columns in the SELECT list, and all the columns referenced in all the expressions are present in the multicolumn index, then the query will use a multicolumn index; for example:

    ```
    SELECT power(x,2), x+y, sin(z) FROM T 
    ORDER BY x,y;
    ```

    In addition to the two previous examples, if the ROWID\(\) function is in the SELECT list expressions, multicolumn indexes will be used. For example:

    ```
    SELECT rowid()+x, z FROM T 
    ORDER BY x,y,z;
    ```

    In addition to the three previous examples, if ROWID\(\) is present at the end of an ORDER BY list, and if the columns of that list — except for ROWID\(\) — use multicolumn indexes in the exact order, multicolumn indexes will be used for the query. For example:

    ```
    SELECT z,y FROM T 
    ORDER BY x,y,z,ROWID();
    ```

    Data lake Relational Engine allows the use of NULL in data values on a user created unique multicolumn HG index, if the column definition allows for NULL values and a constraint \(primary key or unique\) is not being enforced. The rules for this feature are as follows:

    -   A NULL is treated as an undefined value.
    -   Multiple rows with NULL values in a unique index column or columns are allowed.
        1.  In a single column index, multiple rows with a NULL value in an index column are allowed.
        2.  In a multicolumn index, multiple rows with a NULL value in index column or columns are allowed, as long as non-NULL values in the rest of the columns guarantee uniqueness in that index.
        3.  In a multicolumn index, multiple rows with NULL values in all columns participating in the index are allowed.


    These examples illustrate these rules. Given the table table1:

    ```
    CREATE TABLE table1
    (c1 INT NULL, c2 INT NULL, c3 INT NOT NULL);
    ```

    Create a unique single column HG index on a column that allows NULLs:

    ```
    CREATE UNIQUE HG INDEX c1_hg1 ON table1 (c1);
    ```

    According to rule 1 above, you can insert a NULL value into an index column in multiple rows:

    ```
    INSERT INTO table1(c1,c2,c3) VALUES (NULL,1,1);
    INSERT INTO table1(c1,c2,c3) VALUES (NULL,2,2);
    ```

    Create a unique multicolumn HG index on a columns that allows NULLs:

    ```
    CREATE UNIQUE HG INDEX c1c2_hg2 ON table1(c1,c2);
    ```

    According to rule 2 above, you must guarantee uniqueness in the index. The following INSERT does not succeed, since the multicolumn index c1c2\_hg2 on row 1 and row 3 has the same value:

    ```
    INSERT INTO table1(c1,c2,c3) VALUES (NULL,1,3);
    ```

    These INSERT operations are successful, however, according to rules 1 and 3:

    ```
    INSERT INTO table1(c1,c2,c3) VALUES (NULL,NULL,3);
    INSERT INTO table1(c1,c2,c3) VALUES (NULL,NULL,4);
    ```

    Uniqueness is preserved in the multicolumn index.

    This UPDATE operation is successful, as rule 3 allows multiple rows with NULL values in all columns in the multicolumn index:

    ```
    UPDATE table1 SET c2=NULL WHERE c3=1;
    ```

    When a multicolumn HG index is governed by a unique constraint, a NULL value is not allowed in any column participating in the index.

-   You can use the BEGIN PARALLEL IQ … END PARALLEL IQ statement to group CREATE INDEX statements on multiple IQ main store tables, so that they execute as though they are a single DDL statement. See *BEGIN PARALLEL IQ … END PARALLEL IQ Statement* for more information.

> ### Caution:  
> Using the CREATE INDEX command on a local temporary table containing uncommitted data fails and generates the error message ***Local temporary table, *<tablename\>*, must be committed in order to create an index.*** Commit the data in the local temporary table before creating an index.



<a name="loioa617ca4484f21015b2cdfdebbf4a5eee__create_index_privileges1"/>

## Privileges



### 

Requires one of:

-   You own the underlying table of the index.
-   REFERENCES object-level privilege on the table.
-   CREATE ANY INDEX system privilege
-   CREATE ANY OBJECT system privilege
-   CREATE ANY or REFERENCE object-level privilege on the schema containing the underlying table if the schema is owned by another user.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) or [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md) for assistance with granting privileges.



<a name="loioa617ca4484f21015b2cdfdebbf4a5eee__create_index_sideeffects1"/>

## Side Effects

Automatic commit



<a name="loioa617ca4484f21015b2cdfdebbf4a5eee__create_index_standards1"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa617ca4484f21015b2cdfdebbf4a5eee__IQ_Examples"/>

## Examples

-   The following example creates a Compare index on the projected\_earnings and current\_earnings columns. These columns are decimal columns with identical precision and scale:

    ```
    CREATE CMP INDEX proj_curr_cmp
    ON sales_data
    ( projected_earnings, current_earnings );
    ```

-   The following example creates a High\_Group index on the SalesOrderItems table for the ProductID column:

    ```
    CREATE HG INDEX item_prod_hg
    ON Sales_OrderItems
    ( ProductID);
    ```

-   The following example creates a WD index on the earnings\_report table. Specify that the delimiters of strings are space, colon, semicolon, and period. Limit the length of the strings to 25:

    ```
    CREATE WD INDEX earnings_wd
    ON earnings_report_table(varchar)
    DELIMITED BY ‘ :;.’
    LIMIT 25;
    ```

-   The following example creates a DTTM index on the SalesOrders table for the OrderDate column:

    ```
    CREATE DTTM INDEX order_dttm
    ON SalesOrders
    ( OrderDate );
    ```


**Related Information**  


[CREATE INDEX Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/afc9ba646bb842d6b4c5975aa7d17d16.html "Creates an index on a specified table, or pair of tables. Once an index is created, it is never referenced in a SQL statement again except to delete it using the DROP INDEX statement.") :arrow_upper_right:

[ALTER INDEX Statement for Data Lake Relational Engine](alter-index-statement-for-data-lake-relational-engine-a612b20.md "Renames indexes in base or global temporary tables, foreign key role names of indexes and foreign keys explicitly created by a user, or changes the clustered nature of an index on a catalog store table. You can't rename indexes created to enforce key constraints.")

[DROP INDEX Statement for Data Lake Relational Engine](drop-index-statement-for-data-lake-relational-engine-82d6c17.md "Removes an index from the database.")

[BEGIN PARALLEL IQ … END PARALLEL IQ Statement for Data Lake Relational Engine](begin-parallel-iq-end-parallel-iq-statement-for-data-lake-relational-engine-a614601.md "Groups CREATE INDEX statements together for execution at the same time.")

[INDEX\_PREFERENCE Option in Data Lake Relational Engine](../090-database-options/index-preference-option-in-data-lake-relational-engine-a639a2e.md "Controls the choice of indexes to use for queries.")

[FROM Clause for Data Lake Relational Engine](from-clause-for-data-lake-relational-engine-a7749cf.md "Specifies the database tables or views involved in a SELECT statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[REVOKE Object-Level Privilege Statement for Data Lake Relational Engine](revoke-object-level-privilege-statement-for-data-lake-relational-engine-a3e7af2.md "Removes object-level privileges that were given using the GRANT statement.")

[CREATE TEXT INDEX Statement for Data Lake Relational Engine](create-text-index-statement-for-data-lake-relational-engine-a602ced.md "Creates a TEXT index and specifies the text configuration object to use.")

