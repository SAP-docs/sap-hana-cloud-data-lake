<!-- loioa59c232b84f210158782a51ce66730eb -->

# sp\_iqbackupsummary Procedure for Data Lake Relational Engine

Summarizes backup operations performed.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqbackupsummary [ <timestamp> | <backup_id> ]
```



<a name="loioa59c232b84f210158782a51ce66730eb__iq_refbb_1393"/>

## Parameters

 *<timestamp\>* or *<backup\_id\>*
 :   \(Optional\) The interval for which to report backup operations. If you specify *<timestamp\>* or *<backup\_id\>*, only those records with `backup_time` greater than or equal to the time you enter are returned. If you specify no timestamp, the procedure returns all the backup records in ISYSIQBACKUPHISTORY.

 

<a name="loioa59c232b84f210158782a51ce66730eb__section_a2z_n11_nbb"/>

## Returns


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

To run this procedure, you need the EXECUTE privilege on the procedure. See [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md).



<a name="loioa59c232b84f210158782a51ce66730eb__section_kk3_dc1_nbb"/>

## Side Effects

None



<a name="loioa59c232b84f210158782a51ce66730eb__iq_refbb_1398"/>

## Example

Sample output of sp\_iqbackupsummary:

```
backup_id   backup_time             backup_type   selective_type   virtual_type
      883   2008-09-23 13:58:49.0   Full          All inclusive    Non virtual

depends_on_id   creator   backup_size   user_comment   backup_command
            0   DBA                10864               backup database to
                                                         'c:\\\\temp\\\\b1'
```

