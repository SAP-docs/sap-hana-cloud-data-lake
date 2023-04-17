<!-- loio5410af3b00414269988301ba78d38e43 -->

# Promise Module

A Node.js module that exposes Promise-based versions of all asynchronous driver methods.



```
var promiseModule = require('@sap/iq-client/extension/Promise.js');
```



## Members

All functions exposed in the Promise module.



### Functions

All functions in the tables below return a standard Node.js Promise object. All return values are handled using Promise resolution.



<a name="loio5410af3b00414269988301ba78d38e43__section_tfr_nmd_vrb"/>

## Connection Functions


<table>
<tr>
<th valign="top">

Function



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

abort\(ConnObject\)



</td>
<td valign="top">

Aborts the running database request that is being executed on ConnObject.



</td>
</tr>
<tr>
<td valign="top">

clearPool\(ConnObject\)



</td>
<td valign="top">

Empties the connection pool.



</td>
</tr>
<tr>
<td valign="top">

commit\(ConnObject\)



</td>
<td valign="top">

Performs a commit on ConnObject.



</td>
</tr>
<tr>
<td valign="top">

connect\(ConnObject, \{String | Object\}\)



</td>
<td valign="top">

Creates a new connection to the database by using a connection string or a hash of connection parameters that is passed in as a parameter.



</td>
</tr>
<tr>
<td valign="top">

connect\(ConnObject, Number\)



</td>
<td valign="top">

Connects to the database by using an existing connection.



</td>
</tr>
<tr>
<td valign="top">

\{disconnect | close | end\}\(ConnObject\)



</td>
<td valign="top">

Closes the current connection.



</td>
</tr>
<tr>
<td valign="top">

exec\[ute\]\(ConnObject, String\[,Array\]\[,Object\]\)



</td>
<td valign="top">

Executes the specified SQL statement.



</td>
</tr>
<tr>
<td valign="top">

prepare\(ConnObject, String\)



</td>
<td valign="top">

Prepares the specified SQL statement. The returned Promise resolves with a Statement object.



</td>
</tr>
<tr>
<td valign="top">

rollback\(ConnObject\)



</td>
<td valign="top">

Performs a rollback on the ConnObject.



</td>
</tr>
</table>

For more information, see [Connection Class](connection-class-e432e09.md).



<a name="loio5410af3b00414269988301ba78d38e43__section_x2c_smd_vrb"/>

## Statement Functions


<table>
<tr>
<th valign="top">

Function



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

drop\(StatementObject\)



</td>
<td valign="top">

Drops the prepared SQL statement.



</td>
</tr>
<tr>
<td valign="top">

exec\[ute\]\(StatementObject\[,Array\]\[,Object\]\)



</td>
<td valign="top">

Executes the prepared SQL statement.



</td>
</tr>
<tr>
<td valign="top">

exec\[ute\]Batch\(StatementObject\[,Array\]\)



</td>
<td valign="top">

Executes the prepared SQL statement providing an array of parameters.



</td>
</tr>
<tr>
<td valign="top">

exec\[ute\]Query\(StatementObject\[,Array\]\)



</td>
<td valign="top">

Executes the prepared SQL statement. The returned Promise resolves with a ResultSet object.



</td>
</tr>
<tr>
<td valign="top">

getData\(StatementObject, Integer, Integer, Buffer, Integer, Integer\)



</td>
<td valign="top">

Reads a stream of bytes from the specified output LOB parameter.



</td>
</tr>
<tr>
<td valign="top">

getParameterValue\(StatementObject, Integer\)



</td>
<td valign="top">

Retrieves output parameter values.



</td>
</tr>
<tr>
<td valign="top">

sendParameterData\(StatementObject, paramIndex, buffer\)



</td>
<td valign="top">

Sends LOB data to the server in chunks.



</td>
</tr>
</table>

For more information, see [Statement Class](statement-class-3393cbb.md).



<a name="loio5410af3b00414269988301ba78d38e43__section_bhp_ymd_vrb"/>

## ResultSet Functions


<table>
<tr>
<th valign="top">

Function



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

close\(ResultSetObject\)



</td>
<td valign="top">

Closes the ResultSet object and frees up resources.



</td>
</tr>
<tr>
<td valign="top">

getData\(ResultSetObject, Integer, Integer, Buffer, Integer, Integer\)



</td>
<td valign="top">

Reads a stream of bytes from the specified LOB column.



</td>
</tr>
<tr>
<td valign="top">

getValues\(ResultSetObject\[,Options\]\)



</td>
<td valign="top">

Gets an object with the column names and values of the current row.



</td>
</tr>
<tr>
<td valign="top">

next\(ResultSetObject\)



</td>
<td valign="top">

Gets the next row in the result set.



</td>
</tr>
<tr>
<td valign="top">

nextResult\(ResultSetObject\)



</td>
<td valign="top">

Moves to the next result set.



</td>
</tr>
</table>

For more information, see [ResultSet Class](resultset-class-ef7dcb3.md).



<a name="loio5410af3b00414269988301ba78d38e43__section_y2q_cy4_5rb"/>

## Example

> ### Sample Code:  
> ```
> var iq = require('@sap/iq-client');
> var PromiseModule = require('@sap/iq-client/extension/Promise.js');
> var conn = iq.createConnection();
> var result;
> PromiseModule.connect(conn, "serverNode=myserver:443;uid=DBA;pwd=sql")
>   .then(() => {
>        return PromiseModule.prepare(conn, "SELECT 'hello' AS RESULT FROM DUMMY");
>    })
>    .then((stmt) => {
>        return PromiseModule.executeQuery(stmt);
>    })
>    .then((rs) => {
>        result = rs;
>        return PromiseModule.next(result);
>    })
>    .then(() => {
>        return PromiseModule.getValues(result);
>    })
>    .then((row) => {
>        console.log(row);
>        return PromiseModule.close(conn);
>    })
>    .catch(err => {
>        console.log(err);
>    });
> 
> ```

