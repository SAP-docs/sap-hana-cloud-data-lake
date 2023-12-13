<!-- loioa4da9fef84f210159b8ad9de2997c574 -->

# sp\_iqmpxincheartbeatinfo Procedure for Data Lake Relational Engine

If run on the coordinator node, displays INC heartbeat status for every node. If executed on a worker node, displays INC heartbeat status for just the current node.



<a name="loioa4da9fef84f210159b8ad9de2997c574__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqmpxincheartbeatinfo;
```



<a name="loioa4da9fef84f210159b8ad9de2997c574__iq_iqmpx_247"/>

## Result Set


<table>
<tr>
<th valign="top">

Column Name

</th>
<th valign="top">

Data Type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

server\_id

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

Identifier for the node

</td>
</tr>
<tr>
<td valign="top">

server\_name

</td>
<td valign="top">

CHAR\(128\)

</td>
<td valign="top">

Name of the node

</td>
</tr>
<tr>
<td valign="top">

last\_positive\_hb

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Date/time of last successful heartbeat ping, in the following format: DD:MM:YYYY:HH:MM:SS

</td>
</tr>
<tr>
<td valign="top">

time\_not\_responding

</td>
<td valign="top">

TIME

</td>
<td valign="top">

Time since last successful heartbeat ping, in the following format: HH:MM:SS

</td>
</tr>
<tr>
<td valign="top">

time\_until\_timeout

</td>
<td valign="top">

TIME

</td>
<td valign="top">

If a node isn't responding, the time left until node is declared offline.

</td>
</tr>
</table>



<a name="loioa4da9fef84f210159b8ad9de2997c574__iq_iqmpx_248"/>

## Privileges

Requires EXECUTE object-level privilege on the procedure, along with the MANAGE MULTIPLEX system privilege.



## Side Effects

None



<a name="loioa4da9fef84f210159b8ad9de2997c574__iq_iqmpx_251"/>

## Examples

-   Sample output of sp\_iqmpxincheartbeatinfo:

    ```
    server_id,server_name,last_positive_hb,
    time_not_responding,time_until_timeout
    2,'r2_dbsrv90210',2012-11-17
    15:48:42.0,00:00:00,00:00:00
    3,'w3_dbsrv90210',2012-11-17
    15:48:42.0,00:00:00,00:00:00
    ```

-   If the elapsed time exceeds 24 hours, data lake Relational Engine returns sp\_iqmpxincheartbeatinfo output like the following:

    ```
    server_id,server_name,last_positive_hb,
    time_not_responding,time_until_timeout
    2,'r2_mpx_cr_srv',Jan 14 2013 11:57AM,11:59PM,11:59PM
    3,'w4_mpx_cr_srv',Jan 14 2013
    11:57AM,11:59PM,11:59PM
    (2 rows affected) 
    (return status = 0)
    ```

    A value of 11:59PM in the time\_not\_responding and time\_until\_timeout columns means that the time has crossed the 24-hour limit.


