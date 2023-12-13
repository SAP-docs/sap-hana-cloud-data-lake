<!-- loioa59e306484f21015ab9b8d3a215020f9 -->

# sp\_iqclient\_lookup Procedure for Data Lake Relational Engine

Allows a client application to determine the data lake Relational Engine user account responsible for a particular data stream, as observed in a network analyzer originating from a specific client IP address/port.



```
sp_iqclient_lookup [ '<IPaddress>' ], [ <Port> ], [ <UserID> ];
```



## Parameters


<dl>
<dt><b>

*<IPaddress\>*

</b></dt>
<dd>

The IP address of the originating client application.



</dd><dt><b>

*<Port\>*

</b></dt>
<dd>

The port number of the originating client application.



</dd><dt><b>

*<UserID\>*

</b></dt>
<dd>

The data lake Relational Engine user ID.



</dd>
</dl>



## Remarks

The `sp_iqclient_lookup` procedure takes the client IP address and port number and returns a single row containing Number \(the connection ID\), IPaddress, Port, and UserID:

```
sp_iqclient_lookup '158.76.235.71',3360;
```

```
Number   IPaddress      Port    UserID
------   ---------      ----    ------
15       158.76.235.71  3360    rdeniro
```

Optionally, you can pass a third argument to select only the UserID. If no arguments are passed, `sp_iqclient_lookup` returns all current logins with their IP addresses and port numbers. For example:

```
sp_iqclient_lookup;
```

```
Number   IPaddress        Port    UserID
------   ---------        ----    ------
11       162.66.131.36    2082    mbrando
21       162.66.100.233   1863    apacino
22       162.66.100.206   8080    jcaan
23       162.66.100.119   6901    rduvall
24       162.66.100.125   7001    dkeaton
25       162.66.100.124   6347    jcazale

(6 rows affected)
(return status = 0)
```

If a client application is not using TCP/IP or for internal connections, the address appears as 127.0.0.1.

> ### Note:  
> This information is available for logged on users only. No historical login data is kept on the server for this purpose.



<a name="loioa59e306484f21015ab9b8d3a215020f9__iq_refbb_1443"/>

## Privileges

Requires EXECUTE object-level privilege on the procedure, along with one of the following:

-   SELECT ANY TABLE system privilege
-   MONITOR system privilege



## Side Effects

The `sp_iqclient_lookup` stored procedure may impact server performance, which varies from one installation to another. Finding the login name entails scanning through all current active connections on the server; therefore, the impact may be greater on servers with large numbers of connections. Furthermore, this information cannot be cached as it is dynamic — sometimes highly dynamic. It is, therefore, a matter for the local system administrator to manage the use of this stored procedure, as well as monitor the effects on the server, just as for any other client application that uses server facilities.



## Examples

-   The following example shows IP addresses for UserID jcazale:

    ```
    sp_iqclient_lookup null, null, jcazale;
    ```

    ```
    Number   IPaddress        Port    UserID
    ------   ----------       ----    ------
    11       162.66.131.36    2082    jcazale
    15       164.66.131.36    1078    jcazale
    ```

-   The following example shows IP addresses from client IP 162.66.131.36:

    ```
    sp_iqclient_lookup '162.66.131.36';
    ```

    ```
    Number   IPaddress        Port    UserID
    ------   ----------       ----    ------
    11       162.66.131.36    2082    jcazale
    12       162.66.131.36    1078    jcaan
    ```

    > ### Note:  
    > The result is empty when the user specifies an incorrect argument.


