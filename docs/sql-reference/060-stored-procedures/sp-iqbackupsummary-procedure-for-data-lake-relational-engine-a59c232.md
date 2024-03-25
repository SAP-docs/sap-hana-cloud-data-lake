<!-- loioa59c232b84f210158782a51ce66730eb -->

# sp\_iqbackupsummary Procedure for Data Lake Relational Engine

Summarizes backup operations performed.



<a name="loioa59c232b84f210158782a51ce66730eb__section_gkp_cwh_b4b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqbackupsummary [ <timestamp> | <backup_id> ]
```



<a name="loioa59c232b84f210158782a51ce66730eb__iq_refbb_1393"/>

## Parameters


<dl>
<dt><b>

*<timestamp\>* or *<backup\_id\>*

</b></dt>
<dd>

\(Optional\) The interval for which to report backup operations. If you specify *<timestamp\>* or *<backup\_id\>*, only those records with `backup_time` greater than or equal to the time you enter are returned. If you specify no timestamp, the procedure returns all the backup records in ISYSIQBACKUPHISTORY.



</dd>
</dl>



<a name="loioa59c232b84f210158782a51ce66730eb__section_a2z_n11_nbb"/>

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

backup\_id

</td>
<td valign="top">

Identifier for the backup transaction

</td>
</tr>
<tr>
<td valign="top">

backup\_time

</td>
<td valign="top">

Time of the backup

</td>
</tr>
<tr>
<td valign="top">

backup\_type

</td>
<td valign="top">

Type of backup:

-   "Full"
-   "Incremental since incremental"
-   "Incremental since Full"
-   "PITR"



</td>
</tr>
<tr>
<td valign="top">

selective\_type

</td>
<td valign="top">

Subtype of backup:

-   "All inclusive"
-   "All RW files in RW dbspaces"
-   "Set of RO dbspace/file"



</td>
</tr>
<tr>
<td valign="top">

virtual\_type

</td>
<td valign="top">

Type of virtual backup:

-   "Non-virtual"
-   "Decoupled"
-   "Encapsulated"



</td>
</tr>
<tr>
<td valign="top">

depends\_on\_id

</td>
<td valign="top">

Identifier for backup that the backup depends on

</td>
</tr>
<tr>
<td valign="top">

creator

</td>
<td valign="top">

Creator of the backup

</td>
</tr>
<tr>
<td valign="top">

backup\_size

</td>
<td valign="top">

Size, in KB, of the backup

</td>
</tr>
<tr>
<td valign="top">

user\_comment

</td>
<td valign="top">

User comment

</td>
</tr>
<tr>
<td valign="top">

backup\_command

</td>
<td valign="top">

The backup statement issued \(minus the comment\)

</td>
</tr>
</table>



<a name="loioa59c232b84f210158782a51ce66730eb__iq_refbb_1395"/>

## Privileges

Requires EXECUTE object-level privilege on the procedure.



<a name="loioa59c232b84f210158782a51ce66730eb__section_kk3_dc1_nbb"/>

## Side Effects

None



<a name="loioa59c232b84f210158782a51ce66730eb__iq_refbb_1398"/>

## Examples

This example uses the sp\_iqbackupsummary system procedure to return a summary of all backups.


<table>
<tr>
<th valign="top">

backup\_time

</th>
<th valign="top">

backup\_type

</th>
<th valign="top">

selective\_type

</th>
<th valign="top">

virtual\_type

</th>
<th valign="top">

depends\_on\_id

</th>
<th valign="top">

creator

</th>
<th valign="top">

backup\_size

</th>
</tr>
<tr>
<td valign="top">

11:39.0

</td>
<td valign="top">

Virtual cloud

</td>
<td valign="top">

All inclusive

</td>
<td valign="top">

Non virtual

</td>
<td valign="top">

0

</td>
<td valign="top">

saptu

</td>
<td valign="top">

45372

</td>
</tr>
<tr>
<td valign="top">

11:41.0

</td>
<td valign="top">

Virtual cloud

</td>
<td valign="top">

All inclusive

</td>
<td valign="top">

Non virtual

</td>
<td valign="top">

0

</td>
<td valign="top">

saptu

</td>
<td valign="top">

45276

</td>
</tr>
<tr>
<td valign="top">

...

</td>
<td valign="top">

...

</td>
<td valign="top">

...

</td>
<td valign="top">

...

</td>
<td valign="top">

...

</td>
<td valign="top">

...

</td>
<td valign="top">

...

</td>
</tr>
</table>


<table>
<tr>
<th valign="top" colspan="2">

\(Continued\)

</th>
</tr>
<tr>
<th valign="top">

user\_comment

</th>
<th valign="top">

backup\_command

</th>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

backup database virtual cloud to 's3://hdl-backup.dev-eu10.hanacloud/demo-hc-3/backups/XXXXXXXX-6043-XXXX-8704-af61cdfa75bb/vrcloud\_backup\_20230919-011133.bkp' region 'eu-central-1' access\_key\_id 'AKIAXWNIZTPT5JZP74IL' secret\_access\_key '\*\*\*'

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

backup database virtual cloud to 's3://hdl-backup.dev-eu10.hanacloud/demo-hc-3/backups/XXXXXXXX-6043-XXXX-8704-af61cdfa75bb/vrcloud\_backup\_20230919-031136.bkp' region 'eu-central-1' access\_key\_id 'AKIAXWNIZTPT5JZP74IL' secret\_access\_key '\*\*\*'

</td>
</tr>
<tr>
<td valign="top">

...

</td>
<td valign="top">

...

</td>
</tr>
</table>

