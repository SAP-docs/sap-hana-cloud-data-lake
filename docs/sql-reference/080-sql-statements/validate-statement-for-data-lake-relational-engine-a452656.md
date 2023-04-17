<!-- loioa452656484f210159476db66cbecc73a -->

# VALIDATE Statement for Data Lake Relational Engine

Validates the current database, or a single table, materialized view, or index in the IQ catalog \(system\) store.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



> ### Caution:  
> Perform the validation of a table or an entire database only while there are no connections that are making changes to the database; otherwise, errors may be reported indicating some form of database corruption even though no corruption actually exists.



 Syntax 1 – Validates a Database
 :   ```
VALIDATE { CHECKSUM | DATABASE }
```

  Syntax 2 – Validates Tables and Materialized Views
 :   ```
VALIDATE 
   { TABLE [ <owner>.]<table-name>
   | MATERIALIZED VIEW [ { [/pandoc/div/div/horizontalrule/definitionlist/dlentry/dd/codeblock/span/varname
     {"varname"}) <owner> (varname] | [/pandoc/div/div/horizontalrule/definitionlist/dlentry/dd/codeblock/span/varname
     {"varname"}) <schema-name> (varname] }.]<materialized-view-name> }
   [ WITH EXPRESS CHECK ]
```

  Syntax 3 – Validates Indexes
 :   ```
VALIDATE 
   { INDEX <index-name> 
   | [ INDEX ] FOREIGN KEY <role-name> 
   | [ INDEX ] PRIMARY KEY  }
   ON [ { [/pandoc/div/div/horizontalrule/definitionlist/dlentry/dd/codeblock/span/varname
     {"varname"}) <owner> (varname] | [/pandoc/div/div/horizontalrule/definitionlist/dlentry/dd/codeblock/span/varname
     {"varname"}) <schema-name> (varname] }.]{ <table-name> | <materialized-view-name> }
```

  Syntax 4 – Validates Text Indexes
 :   ```
VALIDATE TEXT INDEX <index-name> 
   ON [ { [/pandoc/div/div/horizontalrule/definitionlist/dlentry/dd/codeblock/span/varname
     {"varname"}) <owner> (varname] | [/pandoc/div/div/horizontalrule/definitionlist/dlentry/dd/codeblock/span/varname
     {"varname"}) <schema-name> (varname] }.]<table-name>
```

 

<a name="loioa452656484f210159476db66cbecc73a__IQ_Parameters"/>

## Parameters

 CHECKSUM
 :   Validates the checksum on each page of a database. The CHECKSUM clause ensures that database pages have not been modified on disk. When a database is created with checksums enabled, a checksum is calculated for each database page before it is written to disk. CHECKSUM reads each database page directly from disk — not via the database server's cache — and calculates the checksum for each page. If the calculated checksum for a page does not match the stored checksum for that page, an error occurs and information about the invalid page appears in the database server messages window.

    The CHECKSUM clause is not recommended for databases that have checksums disabled because it reads the entire database from disk.

  DATABASE
 :   Ensures that the free map correctly identifies pages as either allocated or free and that no BLOBs have been orphaned. The DATABASE clause also performs checksum validation and verifies that each database page belongs to the correct object. For example, on a table page, the table ID must identify a valid table whose definition must include the current page in its set of table pages.

    The DATABASE clause brings pages into the database server's cache in sequential order. This results in their validation, as the database server always verifies the contents and checksums of pages brought into the cache. If you start database validation while the database cleaner is running, the validation does not run until the database cleaner is finished running.

  TABLE
 :   Validates the specified table and all of its indexes by checking that the set of all rows and values in the base table matches the set of rows and values contained in each index. The TABLE clause also traverses all the table's BLOBs, verifies BLOB allocation maps, and detects orphaned BLOBs. The TABLE clause checks the physical structure of the table's index pages and verifies the order of the index hash values, and the index's uniqueness requirements \(if any are specified\).

    For foreign key indexes, unless the WITH EXPRESS CHECK clause is specified, each value is looked up in the primary key table to verify that referential integrity is intact. Because the TABLE clause, like the DATABASE clause, uses the database server's cache, the database server also verifies the checksums and basic validity of all pages in use by a table and its indexes.

  INDEX
 :   Performs the same operations as the TABLE clause except that it only validates the specified index and its underlying table; other indexes are not checked.

    For foreign key indexes, unless the WITH EXPRESS CHECK clause is specified, each value is looked up in the primary key table to verify that referential integrity is intact. Specifying the WITH EXPRESS CHECK clause disables referential integrity checking and can therefore significantly improve performance. If the specified index is not a foreign key index, WITH EXPRESS CHECK has no effect.

  TEXT INDEX
 :   Verifies that the positional information for the terms in the index is intact. If the positional information is not intact, an error is generated and you must rebuild the text index. If the text index is either auto or manual, you can rebuild the text index by executing the `REFRESH TEXT INDEX` statement. If the generated error concerns an immediate text index, you must drop the immediate index and create a new one.

 

<a name="loioa452656484f210159476db66cbecc73a__IQ_Permissions"/>

## Privileges

Requires VALIDATE ANY OBJECT system privilege.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



<a name="loioa452656484f210159476db66cbecc73a__IQ_Standards"/>

## Standards

ANSI SQL – compliance level: Transact-SQL extension

**Related Information**  


[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

