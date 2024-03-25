<!-- loio3be5859d6c5f1014a5b99abb9dca0fb0 -->

# sa\_db\_info System Procedure for Data Lake Relational Engine

Reports database property information.



<a name="loio3be5859d6c5f1014a5b99abb9dca0fb0__section_idn_b13_b4b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sa_db_info( [ <dbidparm> ] )
```



## Parameters


<dl>
<dt><b>

*<dbidparm\>* 

</b></dt>
<dd>

Use this optional INTEGER parameter to specify the database ID number. The default is NULL.



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

Number

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Returns the connection ID \(a number\) for the current connection.

</td>
</tr>
<tr>
<td valign="top">

Alias

</td>
<td valign="top">

VARCHAR\(255\)

</td>
<td valign="top">

Returns the database name.

</td>
</tr>
<tr>
<td valign="top">

File

</td>
<td valign="top">

VARCHAR\(255\)

</td>
<td valign="top">

Returns the file name of the database root file, including path.

</td>
</tr>
<tr>
<td valign="top">

ConnCount

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Returns the number of connections to the database. The property value does not include connections used for internal operations, but it does include connections used for events and external environment support.

</td>
</tr>
<tr>
<td valign="top">

PageSize

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Returns the page size of the database, in bytes.

</td>
</tr>
<tr>
<td valign="top">

LogName

</td>
<td valign="top">

VARCHAR\(255\)

</td>
<td valign="top">

Returns the file name of the transaction log, including path.

</td>
</tr>
</table>



## Remarks

If you specify a database ID, sa\_db\_info returns a single row containing the Number, Alias, File, ConnCount, PageSize, and LogName for the specified database.

If *<dbidparm\>* is greater than zero, then properties for the supplied database are returned. If *<dbidparm\>* is less than zero, then properties for the current database are returned. If *<dbidparm\>* is not supplied or is NULL, then properties for all databases running on the database server are returned.



## Privileges

Requires EXECUTE object-level privilege on the procedure. To execute this procedure for other databases, also requires the MONITOR system privilege.



## Side Effects

None



## Examples

This example uses the sa\_db\_info system procedure to return a row for each database that is running on the server:

```
CALL sa_db_info( );
```


<table>
<tr>
<th valign="top">

Number

</th>
<th valign="top">

Alias

</th>
<th valign="top">

File

</th>
<th valign="top">

ConnCount

</th>
<th valign="top">

PageSize

</th>
<th valign="top">

LogName

</th>
</tr>
<tr>
<td valign="top">

0

</td>
<td valign="top">

iqaas

</td>
<td valign="top">

/data\_local/mpx-writer-0-0/iqaas.db

</td>
<td valign="top">

5

</td>
<td valign="top">

4096

</td>
<td valign="top">

/data\_local/mpx-writer-0-0/iqaas\_log.log

</td>
</tr>
</table>

