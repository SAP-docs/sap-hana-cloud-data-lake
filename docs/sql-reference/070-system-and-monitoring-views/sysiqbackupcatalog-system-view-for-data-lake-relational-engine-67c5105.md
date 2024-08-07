<!-- loio67c5105be86d4e919887c93d9f34241e -->

# SYSIQBACKUPCATALOG System View for Data Lake Relational Engine

Maintains complete and up-to-date information of all data lake Relational Engine backups.



<a name="loio67c5105be86d4e919887c93d9f34241e__section_v1w_qbq_b4b"/>

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

Column Constraint

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

bu\_id

</td>
<td valign="top">

UNSIGNED BIGINT

\(xact\_id\)

</td>
<td valign="top">

UNIQUE NOT NULL

\(Primary key; it refers to the bu\_id of SYSIQBACKUPHISTORY

</td>
<td valign="top">

Transaction identifier of the checkpoint of the operation. Backup ID for backup operations.

</td>
</tr>
<tr>
<td valign="top">

type

</td>
<td valign="top">

CHAR\(128\)

</td>
<td valign="top">

NOT NULL

</td>
<td valign="top">

Backup type:

-   Full
-   Incr \(Incremental\)
-   InSF \(Incremental since full\)
-   VRCloud \(Virtual cloud\)



</td>
</tr>
<tr>
<td valign="top">

filename

</td>
<td valign="top">

LONG VARCHAR

</td>
<td valign="top">

NOT NULL

</td>
<td valign="top">

Name of the backup file – contains the full path of the backup destination.

</td>
</tr>
<tr>
<td valign="top">

num\_stripes

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

NOT NULL

</td>
<td valign="top">

The number of backup stripes. The number will be greater than 1 for a multi-striped backup.

</td>
</tr>
<tr>
<td valign="top">

size

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

NOT NULL

</td>
<td valign="top">

Combined size of backup files \(in bytes\).

</td>
</tr>
<tr>
<td valign="top">

dependson\_id

</td>
<td valign="top">

UNSIGNED BIGINT

\(xact\_id\)

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL for full backups.

For incremental or incremental since full backups, the value is dependent on bu\_id.

</td>
</tr>
<tr>
<td valign="top">

start\_time\_utc

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

NOT NULL

</td>
<td valign="top">

Specifies the start time of the backup, given in UTC.

</td>
</tr>
<tr>
<td valign="top">

end\_time\_utc

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

NOT NULL

</td>
<td valign="top">

Specifies the end time of the backup, given in UTC.

</td>
</tr>
<tr>
<td valign="top">

creator

</td>
<td valign="top">

CHAR\(128\)

</td>
<td valign="top">

NOT NULL

</td>
<td valign="top">

Username/ID of the user who issued the backup command.

</td>
</tr>
<tr>
<td valign="top">

offset

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

NOT NULL

</td>
<td valign="top">

The point at which the data backup checkpoint occurs.

</td>
</tr>
<tr>
<td valign="top">

version

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

NOT NULL

</td>
<td valign="top">

Version of the backup catalog.

</td>
</tr>
</table>



<a name="loio67c5105be86d4e919887c93d9f34241e__SYSIQBACKUPCATALOG_remarks1"/>

## Remarks

You can also query SYSIQBACKUPCATALOG as the HDLADMIN user connected to data lake Relational Engine. To do this, use the query:

```
select * from sysiqbackupcatalog;
```

Use the SYSIQBACKUPCATALOG system view to check:

-   which backups exist for your data lake Relational Engine instance.
-   when \(timestamp in utc\) backups of your data lake Relational Engine database were performed.
-   the space consumed by data lake Relational Engine backups on the object store \(this storage incurs cost – you may use the information in the view to double check respective values\).
-   which point can data lake Relational Engine be recovered to if/when you need to perform a recovery.



<a name="loio67c5105be86d4e919887c93d9f34241e__SYSIQBACKUPCATALOG_constraints"/>

## Constraints on Underlying System Table

```
Primary key (bu_id);
```

**Related Information**  


[SYSIQBACKUPCATALOG System View for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/c24ea83905bc44a58a4a04e32863b8ea.html "Maintains complete and up-to-date information of all data lake Relational Engine backups.") :arrow_upper_right:

