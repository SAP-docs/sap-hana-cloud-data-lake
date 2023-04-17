<!-- loioa5d8e3f884f21015b718f5f47b416910 -->

# Tables in the SAP ASE Master Database

Not all SAP Adaptive Server Enterprise master database tables are implemented in the data lake Relational Engine system catalog.


<table>
<tr>
<th valign="top">

Table Name



</th>
<th valign="top">

Description



</th>
<th valign="top">

Data?



</th>
<th valign="top">

Supported by Data Lake Relational Engine?



</th>
</tr>
<tr>
<td valign="top">

`syscharsets`



</td>
<td valign="top">

One row for each character set or sort order



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
</tr>
<tr>
<td valign="top">

`sysconfigures`



</td>
<td valign="top">

One row for each configuration parameter that can be set by a user



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
</tr>
<tr>
<td valign="top">

`syscurconfigs`



</td>
<td valign="top">

Information about configuration parameters currently being used by the server



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
</tr>
<tr>
<td valign="top">

`sysdatabases`



</td>
<td valign="top">

One row for each database on the server



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
</tr>
<tr>
<td valign="top">

`sysdevices`



</td>
<td valign="top">

One row for each disk dump device, disk for databases, and disk partition for databases



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
</tr>
<tr>
<td valign="top">

`sysengines`



</td>
<td valign="top">

One row for each server currently online



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
</tr>
<tr>
<td valign="top">

`syslanguages`



</td>
<td valign="top">

One row for each language \(except U.S. English\) known to the server



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
</tr>
<tr>
<td valign="top">

`syslocks`



</td>
<td valign="top">

Information about active locks



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
</tr>
<tr>
<td valign="top">

`sysloginroles`



</td>
<td valign="top">

One row for each server login that possesses a system-defined role



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
</tr>
<tr>
<td valign="top">

`syslogins`



</td>
<td valign="top">

One row for each valid user account



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
</tr>
<tr>
<td valign="top">

`sysmessages`



</td>
<td valign="top">

One row for each system error or warning



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
</tr>
<tr>
<td valign="top">

`sysprocesses`



</td>
<td valign="top">

Information about server processes



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
</tr>
<tr>
<td valign="top">

`sysremotelogins`



</td>
<td valign="top">

One row for each remote user



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
</tr>
<tr>
<td valign="top">

`syssrvroles`



</td>
<td valign="top">

One row for each server-wide role



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
</tr>
<tr>
<td valign="top">

`sysservers`



</td>
<td valign="top">

One row for each remote server



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
</tr>
<tr>
<td valign="top">

`sysusages`



</td>
<td valign="top">

One row for each disk piece allocated to a database



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
</tr>
</table>

