<!-- loio8bfd6bbf659b4c9ea03236eb2767ec80 -->

# CREATE \(Proxy\) EXISTING TABLE Statement for Data Lake Relational Engine \[SQL on Files\]

Create a new proxy table that represents an existing table on a SQL on Files external catalog.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio8bfd6bbf659b4c9ea03236eb2767ec80__section_fry_b3b_nqb"/>

## Usage

-   This topic is limited to SQL on Files use cases.
-   This SQL on Files SQL statement can be used when connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loio8bfd6bbf659b4c9ea03236eb2767ec80__CET_syntax"/>

## Syntax

```
CREATE EXISTING TABLE [ <owner> .]<proxy-table-name>
   [ ( <column-definition-list> ) ]
   AT '<location-string>'

<column-definition-list> ::=
   <column-name> <data-type>[,<column-name> <data-type>,...]

<location-string> ::=
   <remote-server-name>..<remote-schema-name>.<remote-table-name>
```



<a name="loio8bfd6bbf659b4c9ea03236eb2767ec80__CET_parameters"/>

## Parameters


<dl>
<dt><b>

*<proxy-table-name\>*

</b></dt>
<dd>

The name of the proxy table. The defintion of the proxy table is stored in the data lake Relational Engine catalog.

> ### Note:  
> Tables used as proxy tables cannot have names longer than 30 characters.



</dd><dt><b>

*<column-definition-list\>*

</b></dt>
<dd>

If you do not specify column definitions, data lake Relational Engine derives the column list from the metadata it obtains from the remote table. If you do specify column definitions, data lake Relational Engine verifies them. When data lake Relational Engine checks column names, data types, and lengths:

-   Column names must match identically \(although case is ignored\).
-   Data types in CREATE EXISTING TABLE must match or be convertible to the data types of the column of the remote table. You may encounter some errors if you select from a table in which the data types do not match or other inconsistencies exist.
-   Each column’s length is checked. If the lengths of CHAR, VARCHAR, BINARY, DECIMAL, and NUMERIC columns do not match, a warning message is issued, but the command is not aborted. You might choose to include only a subset of the actual remote column list in your CREATE EXISTING statement.



</dd><dt><b>

AT '*<location-string\>*'

</b></dt>
<dd>

Specifies the location of the remote object. Use a period to delimit the location strings.

The `AT` clause includes a location string that consists of the following parts:

-   The name of the remote server
-   The remote schema
-   The remote table name



</dd>
</dl>



<a name="loio8bfd6bbf659b4c9ea03236eb2767ec80__CET_remarks"/>

## Remarks

The CREATE EXISTING TABLE statement creates a new, local, proxy table that maps to a table in data lake Relational Engine. The EXISTING keyword is used with CREATE TABLE and IN FILES\_SERVICE to specify that a table already exists remotely in SQL on Files, and to import its metadata to the new proxy table. This syntax establishes the remote table as a visible entity to users. The software verifies that the table exists on the SQL on Files remote server before it creates the table.

Data lake Relational Engine proxy tables defined on SQL on Files remote tables are always read only. No DDLs, INSERT, DELETE, or UPDATE statements can be performed on this type of proxy table.

If the remote table does not exist, the statement is rejected with an error message.



## Privileges

You have been granted the HDL\_FILES\_SERVICE\_ADMIN role or the CREATE PROXY TABLE privilege.



<a name="loio8bfd6bbf659b4c9ea03236eb2767ec80__CET_example"/>

## Examples

The following example creates a proxy table named `nation` for the nation table at the remote server `SQLonFilesServer1`:

```
CREATE EXISTING TABLE nation
                            ( n_nationkey int,
                              n_name char(25),
                              n_regionkey int,
                              n_comment char(152)) 
	AT 'SQLonFilesServer1..ExternalSchema1.nation'
```

The following example creates a proxy table named `sof_employee` for the Employees table at the remote server RemoteSOF:

```
CREATE EXISTING TABLE sof_employee
	AT 'RemoteSOF..ExternalSchema1.Employees'
```

**Related Information**  


[CREATE (Proxy) EXISTING TABLE Statement for Data Lake Relational Engine (SAP HANA DB-Managed) \[SQL on Files\]](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/569aa95237b54d28883feeceef487e21.html "Create a new proxy table that represents an existing table on a SQL on Files external catalog.") :arrow_upper_right:

