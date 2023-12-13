<!-- loioa5cad61984f21015a1bd99ca65775698 -->

# SYSIQBACKUPHISTORY System View for Data Lake Relational Engine

This view presents group information from `ISYSIQBACKUPHISTORY` in a readable format. Each row in this view describes a particular backup operation that finished successfully.



<a name="loioa5cad61984f21015a1bd99ca65775698__section_v1w_qbq_b4b"/>

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

</td>
<td valign="top">

NOT NULL

</td>
<td valign="top">

Transaction identifier of the checkpoint of the operation. Backup ID for backup operations.

</td>
</tr>
<tr>
<td valign="top">

bu\_time

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

NOT NULL

</td>
<td valign="top">

Time of backup operation that is recorded in backup record.

</td>
</tr>
<tr>
<td valign="top">

type

</td>
<td valign="top">

TINYINT

</td>
<td valign="top">

NOT NULL

</td>
<td valign="top">

Backup type:

-   0 = FULL
-   1 = INCREMENTAL
-   2 = INCREMENTAL SINCE FULL
-   7 = VRCloud \(Virtual cloud\)



</td>
</tr>
<tr>
<td valign="top">

selective\_type

</td>
<td valign="top">

TINYINT

</td>
<td valign="top">

NOT NULL

</td>
<td valign="top">

Backup subtype:

-   0 = ALL \(backs up all dbfiles\)
-   1 = READ/WRITE ONLY \(backs up all read-write files\)
-   2 = READ ONLY \(backs up a particular read-only file\)



</td>
</tr>
<tr>
<td valign="top">

virtual\_type

</td>
<td valign="top">

TINYINT

</td>
<td valign="top">

NOT NULL

</td>
<td valign="top">

Backup virtual type:

-   0 = NONE
-   1 = DECOUPLED
-   2 = ENCAPSULATED



</td>
</tr>
<tr>
<td valign="top">

dependson\_id

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL for FULL backup.

</td>
</tr>
<tr>
<td valign="top">

cmd

</td>
<td valign="top">

LONG VARCHAR

</td>
<td valign="top">

NOT NULL

</td>
<td valign="top">

Full text of command.

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

User who issued backup command.

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

Backup version.

</td>
</tr>
</table>



<a name="loioa5cad61984f21015a1bd99ca65775698__section_tk4_j4q_qbb"/>

## Remarks

The view SYSIQBACKUP projects equivalent string values for columns type, subtype, and bkp\_virtual.



## Constraints on Underlying System Table

```
Primary key (bu_id);
```

**Related Information**  


[sp\_iqbackupdetails Procedure for Data Lake Relational Engine](../060-stored-procedures/sp-iqbackupdetails-procedure-for-data-lake-relational-engine-a59ba29.md "Shows all the dbfiles included in a particular backup.")

