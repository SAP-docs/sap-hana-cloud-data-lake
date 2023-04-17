<!-- loio9da0c496b1cc4245bae5f9cadf98e5fc -->

# .NET Connection Parameters

Use connection parameters in connection strings to connect and authenticate to a database server.

Specify a connection string in a .NET application when the connection object is created or by setting the ConnectionString property of a connection object.

-   ```
SAConnection conn = new SAConnection("<connection-string>");
```

-   ```
SAConnection conn = new SAConnection();
conn.ConnectionString = "<connection-string>";
```


Specify connection parameters as keyword=value pairs, separated by semicolons. For example:

```
SAConnection conn = new SAConnection(
        "Host=sqla-host:2638;Server=sqla-server;UserID=JSmith;Password=secret");
```

Connection parameter names are case insensitive. For example, `UserID` and `userid` are equivalent. If a connection parameter name contains spaces, then they must be preserved.

Connection parameter values can be case sensitive. For example, passwords are usually case sensitive.



## Connection Parameters


<table>
<tr>
<th valign="top">

Connection Parameter



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

 `Connection lifetime` 



</td>
<td valign="top">

Specifies the maximum lifetime \(in seconds\) for a connection that is to be pooled. If the time between closing a connection and the time it was originally opened is longer than the maximum lifetime, then the connection is not pooled but closed. A connection may have been opened, closed, and pooled many times but when the total lifetime is exceeded, it is no longer returned to the pool. This can result in the pool of available connections shrinking over time. The default is 0, which means no maximum.

```
Connection lifetime=<seconds>
```



</td>
</tr>
<tr>
<td valign="top">

 `Connection timeout` 



</td>
<td valign="top">

Specifies the length of time \(in seconds\) to wait for a connection to the database server before terminating the attempt and generating an error. The default is 15. The alternate form `Connect Timeout` can be used.

```
Connection timeout=<seconds>
```



</td>
</tr>
<tr>
<td valign="top">

 `DatabaseName` 



</td>
<td valign="top">

Identifies the database name. The alternate form `DBN` can be used.

```
DatabaseName=<db-name>
```

This parameter sets the read-only ***Database*** property of the connection object. The property can be queried as follows:

```
String database = conn.Database;
```



</td>
</tr>
<tr>
<td valign="top">

 `Data Source` 



</td>
<td valign="top">

Identifies the data source name. The alternate forms `DataSourceName` and `DSN` can be used.

```
Data Source=<datasource-name>
```



</td>
</tr>
<tr>
<td valign="top">

 `FileDataSourceName` 



</td>
<td valign="top">

Identifies the file data source name. The alternate form `FileDSN` can be used.

```
FileDataSourceName=<file-name>
```



</td>
</tr>
<tr>
<td valign="top">

 `Host` 



</td>
<td valign="top">

Identifies the host computer name or IP address and port number.

```
Host=<host-spec[:host-port]>
```



</td>
</tr>
<tr>
<td valign="top">

 `InitString` 



</td>
<td valign="top">

Specifies a SQL statement that is executed immediately after a connection is established to the database server.

```
InitString=<sql-statement>
```



</td>
</tr>
<tr>
<td valign="top">

 `Max pool size` 



</td>
<td valign="top">

Specifies the maximum size of the connection pool. The default is 100.

```
Max pool size=<number>
```

For example, if Max Pool Size=20, then up to 20 concurrent connections will be pooled when closed. Any concurrent connections beyond the first 20 closed connections will not be pooled \(that is, at most 20 connections will be pooled and the rest will be closed\). Note each pooled connection counts as a "real" connection to the database server. Max Pool Size does not prevent the application from making as many concurrent connections as it desires.

An application that makes at most one connection to the database server at a time will not need to adjust the Min and Max Pool Size settings.



</td>
</tr>
<tr>
<td valign="top">

 `Min pool size` 



</td>
<td valign="top">

Specifies the minimum size of the connection pool. The default is 0.

```
Min pool size=<number>
```

For example, if Min Pool Size=5, then 5 connections are made to the database server at the time the first connection is made. The next 4 concurrent connections will come out of this pool. Any additional concurrent connections are added as needed. This option is useful for multithreaded applications that make several connections where you want a quick response to an "open" request \(the speed is equivalent to unpooling a pooled connection\).

An application that makes at most one connection to the database server at a time will not need to adjust the Min and Max Pool Size settings.



</td>
</tr>
<tr>
<td valign="top">

 `Password` 



</td>
<td valign="top">

Specifies the database user password. The alternate form `PWD` can be used.

```
PWD=<passcode>
```



</td>
</tr>
<tr>
<td valign="top">

 `Persist security info` 



</td>
<td valign="top">

Indicates whether the ***Password*** \(***PWD***\) connection parameter must be retained in the ***ConnectionString*** property of the connection object. The default is ***false***.

```
Persist security info=<boolean-value>
```

When set ***true***, the application can obtain the user's password from the ***ConnectionString*** property if the ***Password*** \(***PWD***\) connection parameter was specified in the original connection string.



</td>
</tr>
<tr>
<td valign="top">

 `Pooling` 



</td>
<td valign="top">

Enables or disables connection pooling. The default is ***true***.

```
Pooling=<boolean-value>
```



</td>
</tr>
<tr>
<td valign="top">

 `Server` 



</td>
<td valign="top">

Identifies the host name and port of the database server. The alternate form `ServerName` can be used.

```
Server=<sqla-server:port>
```

This parameter sets the read-only ***DataSource*** property of the connection object. The property can be queried as follows:

```
String datasource = conn.DataSource;
```



</td>
</tr>
<tr>
<td valign="top">

 `User ID` 



</td>
<td valign="top">

Specifies the database user name. The alternate forms `Username`, `UserID`, and `UID` can be used.

```
UID=<username>
```

> ### Note:  
> Avoid the use of `User ID` in connection strings in application configuration files. `UserID` and `UID` can be used instead.



</td>
</tr>
</table>

Not all connection parameters are described here. For information on other connection parameters, see the topic on database connection parameters.

Note that the ConnectionPool\(CPOOL\) option is ignored by the .NET data provider \(it has no effect at all\).



## Connection String Examples

-   Creates a connection object setting the ConnectionString property and then connects to the database server.

    ```
    SAConnection conn = new SAConnection(
        "Host=sqla-host:2638;Server=sqla-server;UserID=JSmith;Password=secret" );
    conn.Open();
    ```

-   Creates a connection object, sets the ConnectionString property for the connection object, and then connects to the database server. A SET TEMPORARY OPTION statement is executed after connecting to the database server to verify the application signature against the database signature for authenticated applications. Since the SET TEMPORARY OPTION statement contains semicolons, it must be enclosed by quotation marks \("\).

    ```
    SAConnection conn = new SAConnection();
    conn.ConnectionString = 
        "Host=sqla-host:2638;Server=sqla-server;Database=sqla-db;" +
        "UID=JSmith;PWD=secret;" +
        "InitString=\"SET TEMPORARY OPTION connection_authentication=" +
        "'Company=MyCo;" +
        "Application=MyApp;" +
        "Signature=0fa55157edb8e14d818e...'\""
    conn.Open();
    ```

-   Connects to a database server running on the computer identified by an IP address using a user ID and password that were obtained from the user.

    ```
    SAConnection conn = new SAConnection();
    conn.ConnectionString = 
        "Host=10.7.185.43:2638;Server=sqla-server;Database=sqla-db;" +
        "UID=" + user_name + ";PWD=" + pass_code;
    conn.Open();
    ```


