<!-- loiod9c56ecc34a3406886d429c06172573a -->

# CREATE REMOTE SERVER Statement for Data Lake Relational Engine \[SQL on Files\]

Define a remote server using SQL on Files.



<a name="loiod9c56ecc34a3406886d429c06172573a__section_fry_b3b_nqb"/>

## Usage

-   This topic is limited to SQL on Files use cases.
-   This SQL on Files SQL statement can be used when connected directly to data lake Relational Engine as a data lake Relational Engine user.



## Syntax

```
CREATE [REMOTE] SERVER <server-name> CLASS 'FILES_SERVICE'
	READ ONLY [ { ON | VALUE <variable> } ]
```



## Parameters


<dl>
<dt><b>

*<server-name\>*

</b></dt>
<dd>

The server name must be a unique name.



</dd><dt><b>

READ ONLY

</b></dt>
<dd>

Specifies that the remote server is a read-only data source. Any update request is rejected by data lake Relational Engine. `READ ONLY` must be specified. The default is `OFF`.

The `ON` and `VALUE`*<variable\>* clauses are optional, but if the `VALUE`*<variable\>* clause is specified then the value of the variable must be `ON`.

For example:

```
CREATE VARIABLE readonly_var long varchar;
​SET readonly_var = 'on';
​CREATE REMOTE SERVER server1 CLASS 'FILES_SERVICE' READ ONLY readonly_var;
```



</dd>
</dl>



## Remarks

Existing `sp_remote_*` stored procedures and `SYS*` system views work for this type of remote server.



## Privileges

You have been granted the HDL\_FILES\_SERVICE\_ADMIN role.



## Examples

The following example creates the remote server `SQLonFilesServer1` in SQL on Files.

```
CREATE REMOTE SERVER SQLonFilesServer1 CLASS 'FILES_SERVICE'
	READ ONLY
```

**Related Information**  


[DROP \(Remote\) TABLE Statement for Data Lake Relational Engine \[SQL on Files\]](drop-remote-table-statement-for-data-lake-relational-engine-sql-on-files-f81d073.md "Drop a remote table from a SQL on Files external catalog.")

