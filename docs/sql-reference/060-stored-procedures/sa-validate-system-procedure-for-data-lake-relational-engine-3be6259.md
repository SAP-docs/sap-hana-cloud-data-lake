<!-- loio3be625916c5f1014a0f0d4c528aa136a -->

# sa\_validate System Procedure for Data Lake Relational Engine

Validates all or parts of a database.



<a name="loio3be625916c5f1014a0f0d4c528aa136a__section_idn_b13_b4b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sa_validate(
[ <tbl_name>
[, <owner_name> ] ]
[, <check_type> ] ]
[, <isolation_type> ] ]
);
```



## Parameters


<dl>
<dt><b>

*<tbl\_name\>* 

</b></dt>
<dd>

Use this optional CHAR\(128\) parameter to specify the name of a table or materialized view to validate. The default is NULL, in which case the entire database is validated.



</dd><dt><b>

*<owner\_name\>* 

</b></dt>
<dd>

Use this optional CHAR\(128\) parameter to specify an owner. When specified by itself, all tables and materialized views owned by the owner are validated. The default is NULL.



</dd><dt><b>

*<check\_type\>* 

</b></dt>
<dd>

Use this optional CHAR\(10\) parameter to specify the type of validation to perform. The possible values are:


<dl>
<dt><b>

EXPRESS

</b></dt>
<dd>

If this parameter is EXPRESS, each table is checked using a VALIDATE TABLE statement with the WITH EXPRESS CHECK clause.



</dd><dt><b>

NULL

</b></dt>
<dd>

If this parameter is NULL \(the default\), each table is checked using a VALIDATE TABLE statement.



</dd>
</dl>



</dd><dt><b>

*<isolation\_type\>* 

</b></dt>
<dd>

Use this optional parameter when validating tables that have active transactions to prevent receiving false errors about corrupt tables. The possible values are:


<dl>
<dt><b>

DATA LOCK

</b></dt>
<dd>

Prevents transactions from modifying the table schema or data by applying exclusive data locks on the specified tables. Concurrent transactions can read, but not modify the table data or schema.



</dd><dt><b>

SNAPSHOT

</b></dt>
<dd>

Ensures that only committed data is checked by applying snapshot isolation. Transactions can read and modify the data. This clause requires that the database have snapshot isolation enabled \(with the allow\_snapshot\_isolation database option\). Because this clause uses snapshot isolation, performance is often affected.



</dd>
</dl>



</dd>
</dl>



## Result Set


<table>
<tr>
<th valign="top">

Column name

</th>
<th valign="top">

Data type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

Messages

</td>
<td valign="top">

CHAR\(128\)

</td>
<td valign="top">

If validation succeeds without error, then the column contains `No error detected`.

</td>
</tr>
<tr>
<td valign="top">

IsValid

</td>
<td valign="top">

BIT

</td>
<td valign="top">

1 if valid; 0 if validation errors are detected

</td>
</tr>
<tr>
<td valign="top">

ObjectName

</td>
<td valign="top">

CHAR\(261\)

</td>
<td valign="top">

-   Empty string if valid

-   Database if database validation fails

-   The owner and name of a table if table validation fails.




</td>
</tr>
</table>



## Remarks


<table>
<tr>
<th valign="top">

Argument specified

</th>
<th valign="top">

Type of validation

</th>
</tr>
<tr>
<td valign="top">

None

</td>
<td valign="top">

All tables, materialized views, and indexes in the database are validated \(equivalent to a VALIDATE TABLE on every table\). The database itself is also validated \(equivalent to a VALIDATE DATABASE statement\), including checksum validation.

</td>
</tr>
<tr>
<td valign="top">

*<tbl\_name\>* 

</td>
<td valign="top">

If *<owner\_name\>* is NULL, then all tables matching *<tbl\_name\>*, their materialized views, and their indexes are validated.

</td>
</tr>
<tr>
<td valign="top">

*<owner\_name\>* 

</td>
<td valign="top">

All tables, materialized views, and indexes owned by the specified user are validated.

</td>
</tr>
<tr>
<td valign="top">

*<tbl\_name\>* and *<owner\_name\>* 

</td>
<td valign="top">

The specified table or materialized view owned by the specified user, and all of its indexes, are validated.

</td>
</tr>
<tr>
<td valign="top">

*<check\_type\>* 

</td>
<td valign="top">

The specified table\(s\), materialized view\(s\), or index\(es\) is validated using WITH EXPRESS CHECK. The database itself is also validated, including checksum validation.

</td>
</tr>
<tr>
<td valign="top">

*<isolation\_type\>* 

</td>
<td valign="top">

The specified table\(s\), materialized view\(s\), or index\(es\) is validated. Tables either have exclusive data locks applied to them, or only committed data is evaluated. The database itself is also validated, including checksum validation.

</td>
</tr>
</table>

> ### Caution:  
> If *<isolation\_type\>* is not specified, then only perform validation while no connections are making changes to the database; otherwise, false errors may be reported indicating some form of database corruption.

You can validate disk pages for databases that use global or write checksums. If a database has global checksums enabled, then all database pages are validated. If a database has used only write checksums, then only pages with checksums are validated.

For databases with checksums enabled, a checksum is calculated for each database page and this value is stored when the page is written to disk. You can use the Validation utility \(dbvalid\), the VALIDATE statement, the sa\_validate system procedure, or the Validate Database Wizard in SQL Central to perform checksum validation, which consists of reading the database pages from disk and calculating the checksum for the page. If the calculated checksum does not match the stored checksum for a page, the page has been modified or corrupted while on disk or while writing to the page. If one or more pages has been corrupted, an error is returned and information about the invalid pages appears in the database server messages window.



## Privileges

Requires all of:

-   EXECUTE object-level privilege on the procedure
-   VALIDATE ANY OBJECT system privilege



## Side Effects

If *<isolation type\>* is DATA LOCK, then exclusive data locks are applied to the specified table\(s\) or view\(s\).

Automatic commit for both *<isolation\_type\>* options.



## Examples

This example uses the sa\_validate system procedure to validate the database

```
CALL sa_validate( );

```


<table>
<tr>
<th valign="top">

Messages

</th>
<th valign="top">

IsValid

</th>
<th valign="top">

ObjectName

</th>
</tr>
<tr>
<td valign="top">

No error detected

</td>
<td valign="top">

1

</td>
<td valign="top">

 

</td>
</tr>
</table>

This example uses the sa\_validate system procedure to validate the tables and materialized views owned by user USER1:

```
CALL sa_validate('user1');

```


<table>
<tr>
<th valign="top">

Messages

</th>
<th valign="top">

IsValid

</th>
<th valign="top">

ObjectName

</th>
</tr>
<tr>
<td valign="top">

No error detected

</td>
<td valign="top">

0

</td>
<td valign="top">

user1."A1"

</td>
</tr>
</table>

