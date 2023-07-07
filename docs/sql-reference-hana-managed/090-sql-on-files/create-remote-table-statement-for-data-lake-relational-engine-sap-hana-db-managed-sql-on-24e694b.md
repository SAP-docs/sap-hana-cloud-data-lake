<!-- loio24e694b566814ad285cb32fe3e5d3928 -->

# CREATE \(Remote\) TABLE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\) \[SQL on Files\]

Create a remote table managed by SQL on Files.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This topic is limited to SQL on Files use cases.
> 
> This data lake Relational Engine \(SAP HANA DB-Managed\) SQL on Files SQL statement can be used as follows:
> 
> -   When connected to SAP HANA database as a SAP HANA database user.
> 
> -   Using the REMOTE\_EXECUTE procedure. See [REMOTE\_EXECUTE Usage Examples for Executing SQL Statements](../030-sql-statements/remote-execute-usage-examples-for-executing-sql-statements-fd99ac0.md).



## Syntax

```
CREATE [ OR REPLACE ] TABLE [ IF NOT EXISTS ] <remote-schema-name>.<remote-table-name>
    ( <column-definition> ) 
    [ { MANUAL | AUTO } REFRESH ]
    IN FILES_SERVICE

<column-definition> ::=
    <column-name> <data-type>[,.<column-name> <data-type>...]

```



## Parameters


<dl>
<dt><b>

OR REPLACE

</b></dt>
<dd>

If the named table already exists, then drop the existing table and proceed with creation of the new table.



</dd><dt><b>

IF NOT EXISTS

</b></dt>
<dd>

If the named table already exists, no changes are made and an error is not returned.



</dd><dt><b>

*<remote-schema-name\>*

</b></dt>
<dd>

The schema of the table. *<remote-schema-name\>* must be provided.



</dd><dt><b>

*<remote-table-name\>*

</b></dt>
<dd>

The name of the table to be added.



</dd><dt><b>

*<column-name\>*

</b></dt>
<dd>

The name of the column in the table.



</dd><dt><b>

*<data-type\>*

</b></dt>
<dd>

The data type of the column. For SQL on Files

-   `TINYINT` – stores an 8-bit unsigned integer. The minimum value is 0. The maximum value is 255. remote tables, the following data types are supported:

-   `SMALLINT` – stores a 16-bit signed integer. The minimum value is -32,768 \(-2^15\). The maximum value is 32,767 \(2^15-1\).

-   `INTEGER` – stores a 32-bit signed integer. The minimum value is -2,147,483,648 \(-2^31\). The maximum value is 2,147,483,647 \(2^31-1\).

-   `BIGINT` remote – stores a 64-bit signed integer. The minimum value is -9,223,372,036,854,775,808 \(-2^63\). The maximum value is 9,223,372,036,854,775,807 \(2^63-1\).

-   `REAL` – specifies a single-precision 32-bit floating-point number.

-   `DOUBLE` – specifies a double-precision 64-bit floating-point number.

-   `DECIMAL(p, s)` – specifies a fixed-point decimal. `p` specifies precision or the number of total digits \(the sum of whole digits and fractional digits\). `s` denotes scale or the number of fractional digits. Precision `p` can range from 1 to 38. The scale can range from 0 to `p`.

-   `DATE` – consists of year, month, and day to represent a date value. The range of the date value is between 0001-01-01 and 9999-12-31.

-   `TIME` – consists of hour, minute, second, and fractions of seconds. The stored precision is at least 1us.

-   `TIMESTAMP` – consists of date and time information. The stored precision is at least 1us.

-   `VARCHAR(n)` – specifies a variable-length character string, where `n` indicates the maximum length in characters, 1 ≤ n ≤ 5000.




</dd><dt><b>

REFRESH

</b></dt>
<dd>

Controls when the list of data source files for a SQL on Files remote table is updated by performing a directory scan on all current data sources attached to this remote table. The default is `AUTO`.

-   A MANUAL REFRESH updates the table using a REFRESH TABLE statement.

-   An AUTO REFRESH updates the table with every SELECT query on the virtual tables defined on this remote table.




</dd>
</dl>



## Remarks

The SQL on Files external catalog stores the remote table definition.

Columns do not have column constraints. Tables do not have table constraints.

> ### Note:  
> NOT NULL, DEFAULT, CHECK, UNIQUE, PRIMARY KEY, and REFERENCES are not supported.



<a name="loio24e694b566814ad285cb32fe3e5d3928__section_qmw_nnb_nqb"/>

## Privileges

Requires one of:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



## Examples

The following example creates `ExternalTable1`:

```
CREATE TABLE IF NOT EXISTS ExternalSchema1.ExternalTable1 
(
	TS 		TIMESTAMP,
	EQNR 		BIGINT,
	PRESSURE 	DOUBLE,
	OIL_TEMP 	DOUBLE,
	SMPL 		BIGINT 
) IN FILES_SERVICE
```

**Related Information**  


[REMOTE\_EXECUTE Usage Examples for Executing SQL Statements](../030-sql-statements/remote-execute-usage-examples-for-executing-sql-statements-fd99ac0.md "Execute a data lake Relational Engine SQL statement by embedding the statement in the REMOTE_EXECUTE procedure.")

[DROP \(Remote\) TABLE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\) \[SQL on Files\]](drop-remote-table-statement-for-data-lake-relational-engine-sap-hana-db-managed-sql-on-fi-ca1e55d.md "Drop a remote table from a SQL on Files external catalog.")

[ALTER \(Remote\) TABLE Statement with REFRESH for Data Lake Relational Engine \(SAP HANA DB-Managed\) \[SQL on Files\]](alter-remote-table-statement-with-refresh-for-data-lake-relational-engine-sap-hana-db-man-ff7b384.md "Alter the refresh mode of a table.")

[REFRESH \(Remote\) TABLE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\) \[SQL on Files\]](refresh-remote-table-statement-for-data-lake-relational-engine-sap-hana-db-managed-sql-on-054b150.md "Update the current list of data source files for a SQL on Files remote table by performing a directory scan on all current data sources attached to this remote table.")

[CREATE (Remote) TABLE Statement for Data Lake Relational Engine [SQL on Files]](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/beffc07c515540088d372197c9eee191.html "Create a remote table managed by SQL on Files.") :arrow_upper_right:

