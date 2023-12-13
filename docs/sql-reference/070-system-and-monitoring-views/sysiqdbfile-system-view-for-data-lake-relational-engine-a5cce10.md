<!-- loioa5cce10f84f210159e2cec3b04dbc86a -->

# SYSIQDBFILE System View for Data Lake Relational Engine

Presents group information from `ISYSIQDBFILE` in a readable format.



<a name="loioa5cce10f84f210159e2cec3b04dbc86a__section_v1w_qbq_b4b"/>

## Usage

This data lake Relational Engine system view can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



> ### Note:  
> This view replaces the deprecated system view SYSIQFILE.


<table>
<tr>
<th valign="top">

Column Name

</th>
<th valign="top">

Column Type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

dbfile\_id

</td>
<td valign="top">

SMALL INT

</td>
<td valign="top">

Unique ID for the dbfile.

</td>
</tr>
<tr>
<td valign="top">

start\_block

</td>
<td valign="top">

ROWID

</td>
<td valign="top">

Number of the first block.

</td>
</tr>
<tr>
<td valign="top">

block\_count

</td>
<td valign="top">

ROWID

</td>
<td valign="top">

Number of blocks for this file \(dbspace\).

</td>
</tr>
<tr>
<td valign="top">

reserve\_size

</td>
<td valign="top">

ROWID

</td>
<td valign="top">

Pre-allocated storage space for the dbspace.

</td>
</tr>
<tr>
<td valign="top">

allocated

</td>
<td valign="top">

CHAR\(1\)

</td>
<td valign="top">

Defines whether the segment is pre-allocated \(T\) or auto-allocated \(F\).

</td>
</tr>
<tr>
<td valign="top">

data\_offset

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

Identifies the byte location of where the data lake Relational Engine data starts, relative to the beginning of the raw partition.

</td>
</tr>
<tr>
<td valign="top">

create\_time

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Date and time the file was created.

</td>
</tr>
<tr>
<td valign="top">

last\_modified

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Date and time the file was last modified.

</td>
</tr>
<tr>
<td valign="top">

read\_write

</td>
<td valign="top">

CHAR\(1\)

</td>
<td valign="top">

T indicates read-write.

</td>
</tr>
<tr>
<td valign="top">

online

</td>
<td valign="top">

CHAR\(1\)

</td>
<td valign="top">

T indicates online.

</td>
</tr>
<tr>
<td valign="top">

create\_txn\_id

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

Transaction ID that created the dbfile.

</td>
</tr>
<tr>
<td valign="top">

alter\_txn\_id

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

Transaction ID that last modified read\_write status.

</td>
</tr>
<tr>
<td valign="top">

server\_id

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

Multiplex server name.

</td>
</tr>
</table>



## Constraints on Underlying System Table

```
Foreign key (server_id) references SYS.ISYSIQMPXSERVER;
```

```
Unique (server_id, file_name); 
```

