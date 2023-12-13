<!-- loioee4c9163f3a647b3938c7b0c08a9dd44 -->

# CREATE EXISTING TABLE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Creates a new proxy table that represents an existing table on a remote server.



<a name="loioee4c9163f3a647b3938c7b0c08a9dd44__section_kry_1dn_jsb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:

-   Connected to SAP HANA database as a SAP HANA database user and using the SAP HANA database REMOTE\_EXECUTE procedure.



```
CREATE EXISTING [ LOCAL TEMPORARY ] TABLE [ <schema-name>.]<table_name> 
   [ ( <column-definition>, … ) ] 
   AT '<location-string>';
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioee4c9163f3a647b3938c7b0c08a9dd44__section_wt2_3dn_jsb"/>

## Parameters


<dl>
<dt><b>

*<column-definition\>*

</b></dt>
<dd>

Column definitions are required when LOCAL TEMPORARY is specified. Otherwise, column definitions are optional.

```
<column-definition> ::= 
   <column-name> <data-type> [ NOT NULL ];
```

If you do not specify column definitions, data lake Relational Engine derives the column list from the metadata it obtains from the remote table. If you do specify column definitions, data lake Relational Engine verifies them. When data lake Relational Engine checks column names, data types, lengths, and null properties:

-   Column names must match identically \(although case is ignored\).
-   For information on supported data types, see [Available Data Types For CREATE EXISTING TABLE in Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/28c73ef1b8914dc0945dc42e6bc78311.html "A list of available data types when using the CREATE EXISTING TABLE statement in data lake Relational Engine.") :arrow_upper_right:. Data types in CREATE EXISTING TABLE must match or be convertible to the data types of the column on the remote location. For example, a local column data type is defined as NUMERIC, whereas the remote column data type is MONEY. You may encounter some errors, if you select from a table in which the data types do not match or other inconsistencies exist.
-   Each column’s NULL property is checked. If the local column’s NULL property is not identical to the remote column’s NULL property, a warning message is issued, but the statement is not aborted.
-   Each column’s length is checked. If the lengths of CHAR, VARCHAR, BINARY, DECIMAL, and NUMERIC columns do not match, a warning message is issued, but the command is not aborted. You might choose to include only a subset of the actual remote column list in your CREATE EXISTING statement.



</dd><dt><b>

AT '*<location-string\>*'

</b></dt>
<dd>

Specifies the location of the remote object.

```
<location-string> ::=
   <remote-server-name>.[<db-name>].[<owner>].<object-name>
   | <remote-server-name>;[<db-name>];[<owner>];<object-name>;
```

The AT clause supports the semicolon \(;\) as a delimiter. If a semicolon is present anywhere in the *<column-definition\>*, the semicolon is the field delimiter. If no semicolon is present, a period is the field delimiter. This behavior allows file names and extensions to be used in the database and owner fields. An ESCAPE CHARACTER clause allows applications to escape these delimiters within a location string.

When you create a proxy table by using either the CREATE TABLE or the CREATE EXISTING statement, the AT clause includes a location string that consists of the following parts:

-   The name of the remote server
-   The remote catalog
-   The remote owner or schema
-   The remote table name

Use a period or semicolon to delimit the location strings. The location string can also contain variable names that are expanded when the database server evaluates the location string. Variable names within the location string are encapsulated within braces. It is very rare to have a period, semicolon, and a brace, or just a brace, be part of a remote server name, catalog name, owner name, schema name, or table name. However, there may be some situations where one or all of these delimiter characters must be interpreted literally within a location string.

> ### Note:  
> The ESCAPE clause is only necessary if there is a need to escape delimiters within the location clause. In general, the ESCAPE clause can be omitted when creating proxy tables. The escape character can be any single byte character.

The string in the AT clause can contain local or global variable names enclosed in braces \(for example, \{variable-name\}\). The SQL variable name must be of type CHAR, VARCHAR, or LONG VARCHAR. For example, an AT clause that contains 'access;\{@myfile\};;a1' indicates that @myfile is a SQL variable and that the current contents of the @myfile variable should be substituted when the proxy table is created.



</dd>
</dl>



<a name="loioee4c9163f3a647b3938c7b0c08a9dd44__section_szm_jdn_jsb"/>

## Remarks

The CREATE EXISTING TABLE statement creates a new, local, proxy table that maps to a table at an external location. CREATE EXISTING TABLE is a variant of the CREATE TABLE statement. The EXISTING keyword is used with CREATE TABLE to specify that a table already exists remotely, and to import its metadata. This syntax establishes the remote table as a visible entity to users. The software verifies that the table exists at the external location before it creates the table.

The LOCAL TEMPORARY keywords create a data lake Relational Engine table that is private to a connection and destroyed automatically like a local temporary table. In this case, the AT clause must specify '*<data\_lake\_IQ\_instance\>*.*<schema\>*..*<hana\_table\>*'. A column-definition clause is required. The LOCAL TEMPORARY keywords do not import metadata or index information from the SAP HANA database instance. All metadata is obtained from the column-definition clause.

Tables used as proxy tables cannot have names longer than 30 characters.

If the object does not exist \(either as a host data file or remote server object\), the statement is rejected with an error message.

Index information from the host data file or remote server table is extracted and used to create rows for the ISYSIDX system table. This information defines indexes and keys in server terms and enables the query optimizer to consider any indexes that may exist on this table.

Referential constraints are passed to the remote location when appropriate.

You cannot create a proxy table that refers to a remote table on the same node, nor can you create a proxy table that refers to the remote table defined within the multiplex.

For example, in a simplex environment, if you try to create proxy table proxy\_e, which refers to base table Employees defined on the same node, the CREATE EXISTING TABLE statement is rejected with an error message. In a multiplex environment, the CREATE EXISTING TABLE statement is rejected if you create proxy table proxy\_e from any node \(coordinator or secondary\) that refers to remote table Employees defined within a multiplex.

If *<column-definitions\>* are not specified, then the database server derives the column list from the metadata it obtains from the remote table. If column-definitions are specified, then the database server verifies the column-definitions. Column names, data types, lengths, the identity property, and null properties are checked for the following conditions:

-   Column names must match identically \(although case is ignored\).
-   Data types in the CREATE EXISTING TABLE statement must match or be convertible to the data types of the column on the remote location. For example, a local column data type is defined as money, while the remote column data type is numeric.
-   Each column's NULL property is checked. If the local column's NULL property is not identical to the remote column's NULL property, then a warning message is issued, but the statement is not aborted.
-   Each column's length is checked. If the length of CHAR, VARCHAR, BINARY, VARBINARY, DECIMAL and/or NUMERIC columns do not match, then a warning message is issued, but the command is not aborted.

    You may choose to include only a subset of the actual remote column list in your CREATE EXISTING statement. Referential constraints are passed to the remote location when appropriate.




<a name="loioee4c9163f3a647b3938c7b0c08a9dd44__section_tm2_5nr_wwb"/>

## Privileges



### 


<dl>
<dt><b>

Connected to SAP HANA database as a SAP HANA database user and using the SAP HANA database REMOTE\_EXECUTE procedure:

</b></dt>
<dd>

Requires one of:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the SAP HANA database REMOTE\_EXECUTE procedure associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).

-   See [REMOTE\_EXECUTE Guidance and Examples for Executing SQL Statements](remote-execute-guidance-and-examples-for-executing-sql-statements-fd99ac0.md).




</dd>
</dl>



<a name="loioee4c9163f3a647b3938c7b0c08a9dd44__section_ptg_mdn_jsb"/>

## Standards

-   SQL – not in the ISO/ANSI SQL standard.
-   SAP database products – supported by SAP Adaptive Server Enterprise. The format of *<location-string\>* is implementation-defined.



<a name="loioee4c9163f3a647b3938c7b0c08a9dd44__section_orh_rky_gtb"/>

## Examples

-   The following example creates a proxy table named pr\_nation for the nation table at the remote server server\_a, in the database db1, which is owned by joe:

    ```
    CREATE EXISTING TABLE pr_nation
       ( n_nationkey int,
         n_name char(25),
         n_regionkey int,
         n_comment char(152))
       AT 'server_a.db1.joe.nation';
    ```

-   The following example creates a proxy table named pr\_blurbs for the blurbs table at the remote server server\_a. Data lake Relational Engine derives the column list from the metadata it obtains from the remote table:

    ```
    CREATE EXISTING TABLE pr_blurbs AT 'server_a.db1.joe.blurbs';
    ```

-   The following example creates a proxy table named rda\_employee for the Employees table at the data lake Relational Engine remote server remote\_demo\_srv:

    ```
    CREATE EXISTING TABLE rda_employee AT 'remote_demo_srv..dba.Employees';
    ```

-   The following example creates a local temporary proxy table named hana\_employee for the Employees table at the data lake Relational Engine remote server remote\_hana\_srv:

    ```
    CREATE EXISTING LOCAL TEMPORARY TABLE hana_employee
       ( e_empkey int,
         e_surname char(25),
         e_regionkey int,
         e_comment char(152))
       AT 'remote_hana_srv.hana_schema..Employees';
    ```

    In the following example, since the table name \(PROJECT.COMMERCIAL.TABLES :: TT\_ZVBFA\_F\) contains a period, the location string uses semicolons instead of periods.

    ```
    CREATE EXISTING LOCAL TEMPORARY TABLE "VT_TT_ZVBFA" 
       ( VBELV varchar (10),
         POSNV varchar (6),
         VBELN varchar (10),
         POSNN varchar (6),
         VBTYP_N varchar (4),
         VBTYP_V varchar (4),
         ERDAT varchar (8)) 
       AT 'myHANAserver;;PROJECT_1;PROJECT.COMMERCIAL.TABLES :: TT_ZVBFA_F';
    ```


**Related Information**  


[CREATE TABLE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](create-table-statement-for-data-lake-relational-engine-sap-hana-db-managed-6c3afae.md "Creates a new table in the database or on a remote server.")

[ALTER TABLE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](alter-table-statement-for-data-lake-relational-engine-sap-hana-db-managed-593f8b1.md "Modifies a table definition.")

[DROP TABLE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](drop-table-statement-for-data-lake-relational-engine-sap-hana-db-managed-1e62d19.md "Removes a table from the database.")

[CREATE EXISTING TABLE Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/a617378084f21015ab5f9b1b9cfa3620.html "Creates a new proxy table that represents an existing table on a remote server.") :arrow_upper_right:

