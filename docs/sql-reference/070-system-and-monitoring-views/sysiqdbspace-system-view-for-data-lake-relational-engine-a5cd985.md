<!-- loioa5cd985c84f21015a1d0b5c09cd96cb1 -->

# SYSIQDBSPACE System View for Data Lake Relational Engine

Presents group information from `ISYSIQDBSPACE` in a readable format.



<a name="loioa5cd985c84f21015a1d0b5c09cd96cb1__section_v1w_qbq_b4b"/>

## Usage

This data lake Relational Engine system view can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.


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

dbspace\_id

</td>
<td valign="top">

SMALL INT

</td>
<td valign="top">

Each dbspace in a database is assigned a unique number \(dbspace ID\).

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

Time at which the dbspace's read-write status was last modified.

</td>
</tr>
<tr>
<td valign="top">

segment\_type

</td>
<td valign="top">

CHAR\(8\)

</td>
<td valign="top">

Segment type:

-   Main
-   Temp
-   Msg



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

Values:

-   'T' – read writable
-   'F' – read only



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

Values:

-   'T' – online
-   'F' – offline



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

Transaction ID that create the dbspace.

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

striping\_on

</td>
<td valign="top">

CHAR\(1\)

</td>
<td valign="top">

Disk striping:

-   'T' – on
-   'F' – off



</td>
</tr>
<tr>
<td valign="top">

stripe\_size\_kb

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

Number of kilobytes written to each file of the dbspace before the disk striping algorithm moves to the next dbfile.

</td>
</tr>
</table>



## Constraints on Underlying System Table

```
Primary key (dbspace_id);
```

```
Foreign key (dbspace_id) references SYS.ISYSDBSPACE(dbspace_id);
```

