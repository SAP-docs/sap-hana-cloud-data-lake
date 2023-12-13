<!-- loioa4d9bcb384f210159b78b33d0561fa5c -->

# SYSIQMPXSERVER System View for Data Lake Relational Engine

Presents a readable version of the table `ISYSIQMPXSERVER`. The ISYSIQMPXSERVER system table stores membership properties and version status data for the given multiplex node.



<a name="loioa4d9bcb384f210159b78b33d0561fa5c__section_v1w_qbq_b4b"/>

## Usage

This data lake Relational Engine system view can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.




<table>
<tr>
<th valign="top" rowspan="1">

Column Name

</th>
<th valign="top" rowspan="1">

Column Type

</th>
<th valign="top" rowspan="1">

Description

</th>
</tr>
<tr>
<td valign="top" rowspan="1">

server\_id

</td>
<td valign="top" rowspan="1">

UNSIGNED INT NOT NULL

</td>
<td valign="top" rowspan="1">

The ID number of the server.

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

server\_name

</td>
<td valign="top" rowspan="1">

CHAR\(128\) NOT NULL

</td>
<td valign="top" rowspan="1">

The server name; case-insensitive unique.

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

role

</td>
<td valign="top" rowspan="1">

TINYINT NOT NULL

</td>
<td valign="top" rowspan="1">

-   0 – coordinator
-   1 – reader
-   2 – writer



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

status

</td>
<td valign="top" rowspan="1">

TINYINT NOT NULL

</td>
<td valign="top" rowspan="1">

-   0 – included
-   1 – excluded



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

current\_version

</td>
<td valign="top" rowspan="1">

UNSIGNED BIGINT NULL

</td>
<td valign="top" rowspan="1">

Current version ID of the server.

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

active\_version

</td>
<td valign="top" rowspan="1">

LONG BINARY NULL

</td>
<td valign="top" rowspan="1">

The list of active versions on the server \(encoded\).

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

connection\_info

</td>
<td valign="top" rowspan="1">

LONG VARCHAR NULL

</td>
<td valign="top" rowspan="1">

String containing host name and port pairs for public domain connections, delimited by semicolons.

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

db\_path

</td>
<td valign="top" rowspan="1">

LONG VARCHAR NOT NULL

</td>
<td valign="top" rowspan="1">

Full path to the database file for the server.

</td>
</tr>
<tr>
<td valign="top">

private\_connection\_info

</td>
<td valign="top">

LONG VARCHAR NULL

</td>
<td valign="top">

String containing host name and port pairs for private network connections, delimited by semicolons.

</td>
</tr>
</table>



<a name="loioa4d9bcb384f210159b78b33d0561fa5c__section_s5s_qzb_ccb"/>

## Constraints on Underlying System Table

```
Primary key(server_id);
```

