<!-- loio3be657216c5f10148af686ed9c86d496 -->

# sp\_remote\_columns System Procedure for Data Lake Relational Engine

Produce a list of the columns in a remote table, and a description of their data types.



<a name="loio3be657216c5f10148af686ed9c86d496__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_remote_columns (
    <remote-server-name>
    , <remote-table-name>
    [ , <remote-table-owner>
    [ , <table-qualifier> ] ]
);
```



## Parameters


<dl>
<dt><b>

*<remote-server-name\>* 

</b></dt>
<dd>

*<remote-server-name\>* must be specified. Use this CHAR\(128\) parameter to specify the remote server name.



</dd><dt><b>

*<remote-table-name\>* 

</b></dt>
<dd>

Use this optional CHAR\(128\) parameter to specify the name of the remote table. The default is '%'. *<remote-table-name\>* can be specified as null to match any remote table.

> ### Note:  
> If *<remote-table-name\>* is specified, *<remote-table-owner\>* must also be specified.



</dd><dt><b>

*<remote-table-owner\>* 

</b></dt>
<dd>

Use this optional CHAR\(128\) parameter to specify the remote schema name that owns this remote table. The default is '%'.

> ### Note:  
> If *<remote-table-owner\>* is null, Use this optional CHAR\(128\) parameter to specify the database in which *<remote-table-name\>* must also be null, and all remote schemas are returned.



</dd><dt><b>

*<table-qualifier\>* 

</b></dt>
<dd>

*<table-name\>* is located.

> ### Note:  
> *<table-qualifier\>* must be unspecified or null for SQL on Files remote tables.



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

Use this optional CHAR\(128\) parameter to specify the database in whichDescription

</th>
</tr>
<tr>
<td valign="top">

DATABASE

</td>
<td valign="top">

CHAR\(128\)

</td>
<td valign="top">

The database name.

</td>
</tr>
<tr>
<td valign="top">

OWNER

</td>
<td valign="top">

CHAR\(128\)

</td>
<td valign="top">

The remote schema owning the remote table.

</td>
</tr>
<tr>
<td valign="top">

TABLE\_NAME

</td>
<td valign="top">

CHAR\(128\)

</td>
<td valign="top">

The table name.

</td>
</tr>
<tr>
<td valign="top">

COLUMN\_NAME

</td>
<td valign="top">

CHAR\(128\)

</td>
<td valign="top">

The name of a column.

</td>
</tr>
<tr>
<td valign="top">

DOMAIN\_ID

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

An INTEGER that indicates the data type of the column.

</td>
</tr>
<tr>
<td valign="top">

WIDTH

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

The meaning of this column depends on the data type. For character types, width represents the number of characters.

</td>
</tr>
<tr>
<td valign="top">

SCALE

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

The meaning of this column depends on the data type. For NUMERIC data types, scale is the number of digits after the decimal point.

</td>
</tr>
<tr>
<td valign="top">

NULLABLE

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

If NULL column values are allowed, the value is 1. Otherwise, the value is 0.

</td>
</tr>
<tr>
<td valign="top">

BASE\_TYPE\_STR

</td>
<td valign="top">

CHAR\(4096\)

</td>
<td valign="top">

The annotated type string representing the physical type of the column.

</td>
</tr>
</table>



## Remarks

The server definition must be specified depending on the types of tables you reference:

-   For data lake Relational Engine tables, the server must be defined with the [CREATE SERVER Statement for Data Lake Relational Engine](../080-sql-statements/create-server-statement-for-data-lake-relational-engine-a619187.md) to use this system procedure.

-   For SQL on Files tables, the specified server must be defined with the [CREATE REMOTE SERVER Statement for Data Lake Relational Engine \[SQL on Files\]](../100-sql-on-files/create-remote-server-statement-for-data-lake-relational-engine-sql-on-files-d9c56ec.md) to use this system procedure.


If you are entering a CREATE EXISTING TABLE statement and you are specifying a column list, the sp\_remote\_columns system procedure is helpful to get a list of the columns that are available on a remote table.

If the table does not exist on the remote server, the procedure returns an empty result set.



## Privileges

Requires the HDL\_FILES\_SERVICE\_ADMIN role.



## Example

The following example returns information about the columns in the ULProduct table on the remote SQL on Files server named `RemoteSOF` owned by the remote schema RemoteSchema.

```
CALL sp_remote_columns( 'RemoteSOF', 'ULProduct', 'RemoteSchema', null );
```

The following example returns information about the columns in the SOFobjects table using the remote server named RemoteSOF. The table owner is unspecified.

```
CALL sp_remote_columns( 'RemoteSOF', 'SOFobjects', null );
```

The following example returns information about the columns in the ULProduct table on the remote data lake Relational Engine database server named RemoteHDL. The table owner is HDLADMIN.

```
CALL sp_remote_columns( 'RemoteHDL', 'ULProduct', 'HDLADMIN, null );
```

The following example returns information about the columns in the SYSOBJECTS table in the database Production using the remote server named RemoteHDL. The table owner is unspecified.

```
CALL sp_remote_columns( 'RemoteHDL', 'sysobjects', null, 'Production' );
```

The following example returns information about the columns in the Customers table in the Microsoft Access database `c:\users\me\documents\MyAccesDB.accdb` using the remote server MyAccessDB. The Microsoft Access database does not have a table owner so NULL is specified.

```
CALL sp_remote_columns( 'MyAccessDB', 'Customers', null, 'c:\\users\\me\\documents\\MyAccesDB.accdb' );
```

