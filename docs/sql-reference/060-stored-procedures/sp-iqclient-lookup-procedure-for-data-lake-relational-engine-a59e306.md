<!-- loioa59e306484f21015ab9b8d3a215020f9 -->

# sp\_iqclient\_lookup Procedure for Data Lake Relational Engine

Allows a client application to determine the data lake Relational Engine user account responsible for a particular data stream, as observed in a network analyzer originating from a specific client IP address/port.



```
sp_iqclient_lookup [ '<IPaddress>' [, <Port> [, <UserID> ] ] ]
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



<a name="loioa59e306484f21015ab9b8d3a215020f9__section_nzn_bxw_tzb"/>

## Result Set


<table>
<tr>
<th valign="top">

Column Name

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

The connection ID

</td>
</tr>
<tr>
<td valign="top">

IPaddress

</td>
<td valign="top">

The IP address of the originating client application.

</td>
</tr>
<tr>
<td valign="top">

Port

</td>
<td valign="top">

The port number of the originating application.

</td>
</tr>
<tr>
<td valign="top">

UserID

</td>
<td valign="top">

The data lake Relational Engine user ID.

</td>
</tr>
</table>



## Remarks

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

-   This example shows IP addresses for UserID jcazale:

    ```
    sp_iqclient_lookup null, null, jcazale;
    ```


    <table>
    <tr>
    <th valign="top">

    Number
    
    </th>
    <th valign="top">

    IPaddress
    
    </th>
    <th valign="top">

    Port
    
    </th>
    <th valign="top">

    UserID
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    11
    
    </td>
    <td valign="top">
    
    162.66.131.36
    
    </td>
    <td valign="top">
    
    2082
    
    </td>
    <td valign="top">
    
    jcazale
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    15
    
    </td>
    <td valign="top">
    
    164.66.131.36
    
    </td>
    <td valign="top">
    
    1078
    
    </td>
    <td valign="top">
    
    jcazale
    
    </td>
    </tr>
    </table>
    
-   This example shows IP addresses from client IP 162.66.131.36:

    ```
    sp_iqclient_lookup '162.66.131.36';
    ```


    <table>
    <tr>
    <th valign="top">

    Number
    
    </th>
    <th valign="top">

    IPaddress
    
    </th>
    <th valign="top">

    Port
    
    </th>
    <th valign="top">

    UserID
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    11
    
    </td>
    <td valign="top">
    
    162.66.131.36
    
    </td>
    <td valign="top">
    
    2082
    
    </td>
    <td valign="top">
    
    jcazale
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    12
    
    </td>
    <td valign="top">
    
    164.66.131.36
    
    </td>
    <td valign="top">
    
    1078
    
    </td>
    <td valign="top">
    
    jcazale
    
    </td>
    </tr>
    </table>
    

