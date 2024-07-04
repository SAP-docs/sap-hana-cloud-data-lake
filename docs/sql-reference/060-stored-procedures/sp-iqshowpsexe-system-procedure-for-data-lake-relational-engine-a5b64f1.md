<!-- loioa5b64f1584f21015beba9375f49ea0c6 -->

# sp\_iqshowpsexe System Procedure for Data Lake Relational Engine

Displays information about the settings of database options that control the priority of tasks and resource usage for connections.



<a name="loioa5b64f1584f21015beba9375f49ea0c6__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqshowpsexe [ <connection-id> ]
```



<a name="loioa5b64f1584f21015beba9375f49ea0c6__iq_refbb_1754"/>

## Parameters


<dl>
<dt><b>

*<connection-id\>*

</b></dt>
<dd>

\(Optional\) An integer representing the connection ID.

If *<connection-id\>* is specified, sp\_iqshowpsexe returns information only about the specified connection. If *<connection-id\>* is not specified, sp\_iqshowpsexe returns information about all connections.

If the specified connection-id does not exist, sp\_iqshowpsexe returns no rows.



</dd>
</dl>



<a name="loioa5b64f1584f21015beba9375f49ea0c6__section_ptp_hc4_nbb"/>

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

connectionid

</td>
<td valign="top">

The connection ID

</td>
</tr>
<tr>
<td valign="top">

application

</td>
<td valign="top">

Information about the client application that opened the connection. Includes the AppInfo connection property information:

-   HOST – the host name of the client machine
-   APPINFO – the APPINFO in the client connection string, if specified



</td>
</tr>
<tr>
<td valign="top">

userid

</td>
<td valign="top">

Login name of the user that opened the connection

</td>
</tr>
<tr>
<td valign="top">

iqgovern\_priority

</td>
<td valign="top">

Value of the database option IQGOVERN\_PRIORITY that assigns a priority to each query waiting in the -iqgovern queue. By default, this option has a value of 2 \(MEDIUM\). The values 1, 2, and 3 are shown as HIGH, MEDIUM, and LOW, respectively.

</td>
</tr>
<tr>
<td valign="top">

max\_query\_time

</td>
<td valign="top">

Value of the database option MAX\_QUERY\_TIME that sets a limit, so that the optimizer can disallow very long queries. By default, this option is disabled and has a value of 0.

</td>
</tr>
<tr>
<td valign="top">

query\_row\_limit

</td>
<td valign="top">

Value if the database option QUERY\_ROWS\_RETURNED\_LIMIT that sets the row threshold for rejecting queries based on the estimated size of the result set. The default is 0, which means there is no limit.

</td>
</tr>
<tr>
<td valign="top">

query\_temp\_space\_limit

</td>
<td valign="top">

Value of the database option QUERY\_TEMP\_SPACE\_LIMIT \(in MB\) that constrains the use of temporary IQ dbspace by user queries. The default value is 2000 MB.

</td>
</tr>
<tr>
<td valign="top">

max\_cursors

</td>
<td valign="top">

Value of the database option MAX\_CURSOR\_COUNT that specifies a resource governor to limit the maximum number of cursors a connection can use at once. The default value is 50. A value of 0 implies no limit.

</td>
</tr>
<tr>
<td valign="top">

max\_statements

</td>
<td valign="top">

Value of the database option MAX\_STATEMENT\_COUNT that specifies a resource governor to limit the maximum number of prepared statements that a connection can use at once. The default value is 100. A value of 0 implies no limit.

</td>
</tr>
</table>



<a name="loioa5b64f1584f21015beba9375f49ea0c6__iq_refbb_1756"/>

## Remarks

The sp\_iqshowpsexe stored procedure displays information about the settings of database options that control the priority of tasks and resource usage for connections, which is useful to database administrators for performance tuning.

> ### Note:  
> The AppInfo property may not be available from Open Client or jConnect applications such as Interactive SQL. If the AppInfo property is not available, the application column is blank.



<a name="loioa5b64f1584f21015beba9375f49ea0c6__iq_refbb_1753"/>

## Privileges

Requires all of the following:

-   EXECUTE object-level privilege on this procedure
-   MONITOR system privilege



## Side Effects

None.



<a name="loioa5b64f1584f21015beba9375f49ea0c6__iq_refbb_1758"/>

## Examples

This example returns information about all of the database options that control the priority of tasks and resource usage.

```
CALL sp_iqshowpsexe;
```


<table>
<tr>
<th valign="top">

connectionid

</th>
<th valign="top">

application

</th>
<th valign="top">

userid

</th>
<th valign="top">

iqgovern\_

priority

</th>
<th valign="top">

max\_

query\_

time

</th>
<th valign="top">

query\_

row\_

limit

</th>
<th valign="top">

query\_

temp\_

space

</th>
<th valign="top">

max\_

statements

</th>
<th valign="top">

max\_

cursors

</th>
</tr>
<tr>
<td valign="top">

223272

</td>
<td valign="top">

HOST=hana-tooling-hrtt-svc-XXXXXX-XXXXXX-XXXXXX;EXE=/usr/local/bin/node;

</td>
<td valign="top">

HDLADMIN

</td>
<td valign="top">

MEDIUM

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

100

</td>
<td valign="top">

50

</td>
</tr>
<tr>
<td valign="top">

227218

</td>
<td valign="top">

HOST=hana-tooling-hrtt-svc-XXXXXX-XXXXXX-XXXXXX;EXE=/usr/local/bin/node;

</td>
<td valign="top">

HDLADMIN

</td>
<td valign="top">

MEDIUM

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

100

</td>
<td valign="top">

50

</td>
</tr>
<tr>
<td valign="top">

237715

</td>
<td valign="top">

HOST=hana-tooling-hrtt-svc-XXXXXX-XXXXXX-XXXXXX;EXE=/usr/local/bin/node;

</td>
<td valign="top">

USER1

</td>
<td valign="top">

MEDIUM

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

100

</td>
<td valign="top">

50

</td>
</tr>
<tr>
<td valign="top">

1000000004

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

MEDIUM

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

100

</td>
<td valign="top">

50

</td>
</tr>
</table>

**Related Information**  


[CONNECTION\_PROPERTY Function \[System\] for Data Lake Relational Engine](../050-system-sql-functions/connection-property-function-system-for-data-lake-relational-engine-a53eeaf.md "Returns the value of a given connection property as a string.")

