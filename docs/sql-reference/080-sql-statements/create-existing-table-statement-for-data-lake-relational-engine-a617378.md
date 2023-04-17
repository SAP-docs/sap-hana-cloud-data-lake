<!-- loioa617378084f21015ab5f9b1b9cfa3620 -->

# CREATE EXISTING TABLE Statement for Data Lake Relational Engine

Creates a new proxy table that represents an existing table on a remote server.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
CREATE EXISTING [ LOCAL TEMPORARY ] TABLE [ { [/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <owner> (varname] | [/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <schema-name> (varname] }.]<table_name> 
   [ ( <column-definition>, … ) ] 
   AT '<location-string>'
```



<a name="loioa617378084f21015ab5f9b1b9cfa3620__create_existing_table_parm1"/>

## Parameters

 *<column-definition\>*
 :   Column definitions are required when LOCAL TEMPORARY is specified. Otherwise, column definitions are optional.

    ```
    <column-definition> ::= 
       <column-name> <data-type> [ NOT NULL ]
    ```

    If you do not specify column definitions, data lake Relational Engine derives the column list from the metadata it obtains from the remote table. If you do specify column definitions, data lake Relational Engine verifies them. When data lake Relational Engine checks column names, data types, lengths, and null properties:

    -   Column names must match identically \(although case is ignored\).
    -   For information on supported data types, see [Available Data Types For CREATE EXISTING TABLE in Data Lake Relational Engine](available-data-types-for-create-existing-table-in-data-lake-relational-engine-28c73ef.md). Data types in CREATE EXISTING TABLE must match or be convertible to the data types of the column on the remote location. For example, a local column data type is defined as NUMERIC, whereas the remote column data type is MONEY. You may encounter some errors, if you select from a table in which the data types do not match or other inconsistencies exist.
    -   Each column’s NULL property is checked. If the local column’s NULL property is not identical to the remote column’s NULL property, a warning message is issued, but the statement is not aborted.
    -   Each column’s length is checked. If the lengths of CHAR, VARCHAR, BINARY, DECIMAL, and NUMERIC columns do not match, a warning message is issued, but the command is not aborted. You might choose to include only a subset of the actual remote column list in your CREATE EXISTING statement.

  AT '*<location-string\>*'
 :   Specifies the location of the remote object.

    ```
    <location-string> ::=
       <remote-server-name>.[<db-name>].[<owner>].<object-name>
       | <remote-server-name>;[<db-name>];[<owner>];<object-name>
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

 

<a name="loioa617378084f21015ab5f9b1b9cfa3620__create_existing_table_remarks"/>

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




<a name="loioa617378084f21015ab5f9b1b9cfa3620__create_existing_table_privileges1"/>

## Privileges



### 

-   To create a self owned table requires one of:
    -   CREATE PROXY TABLE system privilege

-   To create a table owned by another user requires one of:
    -   CREATE ANY TABLE system privilege
    -   CREATE ANY OBJECT system privilege
    -   CREATE ANY object-level privilege on the schema to contain the table if the schema is owned by another user.


See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



<a name="loioa617378084f21015ab5f9b1b9cfa3620__create_existing_table_standards1"/>

## Standards

-   SQL – not in the ISO/ANSI SQL standard.
-   SAP database products – supported by SAP Adaptive Server Enterprise. The format of *<location-string\>* is implementation-defined.



<a name="loioa617378084f21015ab5f9b1b9cfa3620__create_existing_table_examples1"/>

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


[CREATE TABLE Statement for Data Lake Relational Engine](create-table-statement-for-data-lake-relational-engine-a619764.md "Creates a new table in the database or on a remote server.")

[DROP Statement for Data Lake Relational Engine](drop-statement-for-data-lake-relational-engine-a61c216.md "Removes objects from the database.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[CREATE EXISTING TABLE Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/ee4c9163f3a647b3938c7b0c08a9dd44.html "Creates a new proxy table that represents an existing table on a remote server.") :arrow_upper_right:

