<!-- loio934f35e295c847698eb5c9e96e26efa9 -->

# Node.js Connection Properties

When connecting to data lake Relational Engine using Node.js, you can specify connection properties. Property names are case insensitive.



> ### Note:  
> Do not set connection properties to an empty string. The client will substitute any empty string values with the property's default setting.



The following table lists the data lake client-specific Node.js connection properties.


<table>
<tr>
<th valign="top">

Property



</th>
<th valign="top">

Value



</th>
<th valign="top">

Default



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

`charset`



</td>
<td valign="top">

 *<character-set\>* 



</td>
<td valign="top">



</td>
<td valign="top">

Specifies the character set. This value must be either "ASCII", "UTF-8", or "UCS2".



</td>
</tr>
<tr>
<td valign="top">

`connectionLifetime`



</td>
<td valign="top">

 *<number\>* 



</td>
<td valign="top">

0



</td>
<td valign="top">

Specifies the maximum time, in seconds, that the connection is cached in the pool. A value of 0 causes pooled connections to be cached permanently.

When a pooled connection is closed, its creation time is compared with the current time, and the connection is disrupted if that time span \(in seconds\) exceeds the value specified by `connectionLifetime`. Otherwise, the connection is returned to the connection pool for future reuse.



</td>
</tr>
<tr>
<td valign="top">

`dbn` | `databaseName`



</td>
<td valign="top">

 *<name\>* 



</td>
<td valign="top">



</td>
<td valign="top">

Specifies the name of the database to connect to.



</td>
</tr>
<tr>
<td valign="top">

`dataTruncationError`



</td>
<td valign="top">

Boolean



</td>
<td valign="top">

FALSE



</td>
<td valign="top">

When set to TRUE, fails the stored procedure call whenever a data truncation error occurs.



</td>
</tr>
<tr>
<td valign="top">

`host`



</td>
<td valign="top">

 *<host-name\>* 



</td>
<td valign="top">



</td>
<td valign="top">

Specifies the name of the host to connect to.



</td>
</tr>
<tr>
<td valign="top">

`maxPoolSize`



</td>
<td valign="top">

 *<number\>* 



</td>
<td valign="top">

0



</td>
<td valign="top">

Defines the maximum number of connections that are allowed in the connection pool.

The default value is 0, meaning there is no limit.



</td>
</tr>
<tr>
<td valign="top">

`pooling`



</td>
<td valign="top">

Boolean



</td>
<td valign="top">

FALSE



</td>
<td valign="top">

Specifies whether the node.js driver opens a pooled connection. Connection pools can improve performance for opening connections.

Set pooling to TRUE to use connection pools.



</td>
</tr>
<tr>
<td valign="top">

`port`



</td>
<td valign="top">

 *<port-number\>* 



</td>
<td valign="top">



</td>
<td valign="top">

Specifies the port number to connect to.



</td>
</tr>
<tr>
<td valign="top">

`pwd` | `password`



</td>
<td valign="top">

 *<password\>* 



</td>
<td valign="top">



</td>
<td valign="top">

Specifies the password for the data lake Relational Engine user.



</td>
</tr>
<tr>
<td valign="top">

`resultSetArrayLimitMB`



</td>
<td valign="top">

*<number\>* in MB



</td>
<td valign="top">

2048 \(2 GB\)



</td>
<td valign="top">

Limits the maximum amount of memory used for result set arrays returned by Connection.exec\[ute\] and Statement.exec\[ute\]. This can be helpful for applications that need to limit the maximum amount of memory used by the node process. The value is in MB and limits the approximate total amount of data in the result set before returning an error. The maximum value allowed is 2048 \(2 GB\). Specifying 0, any value greater than 2048, or a noninteger value defaults to 2048.

> ### Note:  
> The actual maximum amount of memory used by the various layers can be higher than the value of `resultSetArrayLimitMB`. For example, if `resultSetArrayLimitMB` is set to 10, the data for each result set is limited to approximately 10 MB, but a 10 MB result set could use 20 MB or more of peak memory during the node process.



</td>
</tr>
<tr>
<td valign="top">

`uid` | `user`



</td>
<td valign="top">

 *<user-ID\>* 



</td>
<td valign="top">



</td>
<td valign="top">

Specifies the name of a data lake Relational Engine user.



</td>
</tr>
</table>

**Related Information**  


[Encryption \(ENC\) Connection Parameter](https://help.sap.com/docs/SAP_HANA_DATA_LAKE/a895964984f210158925ce02750eb580/81408d9a6ce2101493b9c3bd4a39e77e.html)

