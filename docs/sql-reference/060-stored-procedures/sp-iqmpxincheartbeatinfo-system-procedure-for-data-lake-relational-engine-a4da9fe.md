<!-- loioa4da9fef84f210159b8ad9de2997c574 -->

# sp\_iqmpxincheartbeatinfo System Procedure for Data Lake Relational Engine

If run on the coordinator node, displays INC heartbeat status for every node. If executed on a worker node, displays INC heartbeat status for just the current node.



<a name="loioa4da9fef84f210159b8ad9de2997c574__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqmpxincheartbeatinfo
```



<a name="loioa4da9fef84f210159b8ad9de2997c574__section_i3l_yfb_mbc"/>

## Parameters

None



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

Requires all of the following:

-   EXECUTE object-level privilege on this procedure.
-   MANAGE MULTIPLEX system privilege



## Side Effects

None.



<a name="loioa4da9fef84f210159b8ad9de2997c574__iq_iqmpx_251"/>

## Examples

This example returns INC heartbeat status information.

```
CALL sp_iqmpxincheartbeatinfo;
```


<table>
<tr>
<th valign="top">

server\_id

</th>
<th valign="top">

server\_name

</th>
<th valign="top">

last\_positive\_hb

</th>
<th valign="top">

time\_not\_responding

</th>
<th valign="top">

time\_until\_timeout

</th>
</tr>
<tr>
<td valign="top">

2

</td>
<td valign="top">

mpx-writer-0-0

</td>
<td valign="top">

2024-05-21 14:13:06.000000

</td>
<td valign="top">

00:00.0

</td>
<td valign="top">

00:00.0

</td>
</tr>
</table>

If the elapsed time exceeds 24 hours, data lake Relational Engine returns sp\_iqmpxincheartbeatinfo output similar to the following:


<table>
<tr>
<th valign="top">

server\_id

</th>
<th valign="top">

server\_name

</th>
<th valign="top">

last\_positive\_hb

</th>
<th valign="top">

time\_not\_responding

</th>
<th valign="top">

time\_until\_timeout

</th>
</tr>
<tr>
<td valign="top">

2

</td>
<td valign="top">

mpx-writer-0-0

</td>
<td valign="top">

2024-04-15 11:57 AM

</td>
<td valign="top">

11:59PM

</td>
<td valign="top">

11:59PM

</td>
</tr>
<tr>
<td valign="top" colspan="5">

\(2 rows affected\)

</td>
</tr>
<tr>
<td valign="top" colspan="5">

\(return status = 0\)

</td>
</tr>
</table>

A value of 11:59PM in the time\_not\_responding and time\_until\_timeout columns means that the time has crossed the 24-hour limit.

