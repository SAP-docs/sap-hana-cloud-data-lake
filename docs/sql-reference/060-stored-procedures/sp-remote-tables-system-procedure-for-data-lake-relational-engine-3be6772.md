<!-- loio3be677246c5f101491d2a9a435e92f1f -->

# sp\_remote\_tables System Procedure for Data Lake Relational Engine

Return a list of the tables on a remote server.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loio3be677246c5f101491d2a9a435e92f1f__section_dkt_llj_n4b"/>

## Syntax

```
sp_remote_tables (
    <remote-server-name>
    [ , <remote-table-name>
    [ , <remote-table-owner>
    [ , <remote-database-name>
    [ , <with-table-type> ] ] ] ]
)

```



## Parameters

  *<remote-server-name\>* 
 :   Use this CHAR\(128\) parameter to specify the remote server name. *<remote-server-name\>* must be specified.

   *<remote-table-name\>* 
 :   Use this optional CHAR\(128\) parameter to specify the name of the remote table. The default is '%'. *<remote-table-name\>* can be specified as null to match any remote table.

    > ### Note:  
    > If *<remote-table-name\>* is specified, *<remote-table-owner\>* must also be specified.

   *<remote-table-owner\>* 
 :   Use this optional CHAR\(128\) parameter to specify the remote schema name that owns this remote table. The default is '%'.

    > ### Note:  
    > If *<remote-table-owner\>* is null, *<remote-table-name\>* must also be null, and all remote schemas are returned.

   *<remote-database-name\>* 
 :   Use this optional CHAR\(128\) parameter to specify the database in which *<table-name\>* is located.

    > ### Note:  
    > *<remote-database-name\>* must be unspecified or null for SQL on Files remote tables.

   *<with-table-type\>* 
 :   Use this optional BIT parameter to specify the inclusion of remote table types. The default is 0. Specify 1 if you want the result set to include a column that lists table types or specify 0 if you do not.

 

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

DATABASE



</td>
<td valign="top">

CHAR\(128\)



</td>
<td valign="top">

The name of the remote database.



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

The name of the table.



</td>
</tr>
<tr>
<td valign="top">

TABLE\_TYPE



</td>
<td valign="top">

CHAR\(128\)



</td>
<td valign="top">

Specifies the table type. The values depend on the type of remote server.



</td>
</tr>
</table>



## Remarks

The server definition must be specified depending on the types of tables you reference:

-   For data lake Relational Engine tables, the server must be defined using the [CREATE SERVER Statement for Data Lake Relational Engine](../080-sql-statements/create-server-statement-for-data-lake-relational-engine-a619187.md).

-   For SQL on Files tables, the specified server must be defined using the [CREATE REMOTE SERVER Statement for Data Lake Relational Engine \[SQL on Files\]](../100-sql-on-files/create-remote-server-statement-for-data-lake-relational-engine-sql-on-files-d9c56ec.md).


It may be helpful when you are configuring your remote server to get a list of the remote tables available on a particular server. This procedure returns a list of the tables on a server.

The procedure accepts five parameters. If a table or schema name is given, the list of tables will be limited to only those that match the arguments.



## Privileges

You must have EXECUTE privilege on the system procedure.



<a name="loio3be677246c5f101491d2a9a435e92f1f__section_y4g_tys_5wb"/>

## Example

The following example returns information about the tables owned by the remote schema RemoteSchema in a SQL on Files remote server named RemoteSOF.

```
CALL sp_remote_tables( 'RemoteSOF', null, 'RemoteSchema' );
```

The following example returns a list of all the remote tables in the remote server named RemoteSOF:

```
CALL sp_remote_tables( 'RemoteSOF', null, 'null' );
```

The following example returns information about the tables owned by USER1 in a data lake Relational Engine remote server named MyRemoteServerr.

```
CALL sp_remote_tables( 'MyRemoteServer', null, 'USER1' );
```

The following example returns a list of all the tables owned by Fred in the my\_customers database in a remote server named RemoteASE:

```
CALL sp_remote_tables( 'RemoteASE', null, 'Fred', 'my_customers' );
```
