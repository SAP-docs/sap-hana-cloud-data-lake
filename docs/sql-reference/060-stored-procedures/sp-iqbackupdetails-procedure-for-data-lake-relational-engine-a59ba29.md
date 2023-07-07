<!-- loioa59ba29984f210158062fc278ebdfdba -->

# sp\_iqbackupdetails Procedure for Data Lake Relational Engine

Shows all the dbfiles included in a particular backup.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqbackupdetails <backup_id> 
```



<a name="loioa59ba29984f210158062fc278ebdfdba__iq_refbb_1386"/>

## Parameters


<dl>
<dt><b>

*<backup\_id\>*

</b></dt>
<dd>

The backup operation transaction identifier.



</dd>
</dl>



<a name="loioa59ba29984f210158062fc278ebdfdba__section_arw_w11_nbb"/>

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

Identifier for the backup transaction.



</td>
</tr>
<tr>
<td valign="top">

backup\_time



</td>
<td valign="top">

Time of the backup.



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
-   "Incremental since full"



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

depends\_on\_id



</td>
<td valign="top">

Identifier for previous backup that the backup depends on.



</td>
</tr>
<tr>
<td valign="top">

dbspace\_id



</td>
<td valign="top">

Identifier for the dbspace being backed up.



</td>
</tr>
<tr>
<td valign="top">

dbspace\_name



</td>
<td valign="top">

Name of the dbspace from SYSIQBACKUPHISTORYDETAIL. If dbspace name matches the dbspace name in SYSDBSPACE for a given dbspace\_id. Otherwise "null."



</td>
</tr>
<tr>
<td valign="top">

dbspace\_rwstatus



</td>
<td valign="top">

"ReadWrite" or "Read Only."



</td>
</tr>
<tr>
<td valign="top">

dbspace\_createid



</td>
<td valign="top">

Dbspace creation transaction identifier.



</td>
</tr>
<tr>
<td valign="top">

dbspace\_online



</td>
<td valign="top">

Status "Online" or "Offline."



</td>
</tr>
<tr>
<td valign="top">

dbspace\_size



</td>
<td valign="top">

Size of dbspace, in KB, at time of backup.



</td>
</tr>
<tr>
<td valign="top">

dbspace\_backup\_size



</td>
<td valign="top">

Size of data, in KB, backed up in the dbspace.



</td>
</tr>
<tr>
<td valign="top">

dbfile\_id



</td>
<td valign="top">

Identifier for the dbfile being backed up.



</td>
</tr>
<tr>
<td valign="top">

dbfile\_name



</td>
<td valign="top">

The logical file name, if it was not renamed after the backup operation. If renamed, "null."



</td>
</tr>
<tr>
<td valign="top">

dbfile\_rwstatus



</td>
<td valign="top">

"ReadWrite" or "Read Only."



</td>
</tr>
<tr>
<td valign="top">

dbfile\_createid



</td>
<td valign="top">

Dbfile creation transaction identifier.



</td>
</tr>
<tr>
<td valign="top">

dbfile\_size in MB



</td>
<td valign="top">

Size of the dbfile, in MB.



</td>
</tr>
<tr>
<td valign="top">

dbfile\_backup\_size



</td>
<td valign="top">

Size of the dbfile backup, in KB.



</td>
</tr>
<tr>
<td valign="top">

dbfile\_path



</td>
<td valign="top">

The dbfile path from SYSBACKUPDETAIL, if it matches the physical file path \("file\_name"\) in SYSDBFILE for a given dbspace\_id and the dbfile\_id. Otherwise "null."



</td>
</tr>
</table>



<a name="loioa59ba29984f210158062fc278ebdfdba__iq_refbb_1389"/>

## Remarks

To obtain the backup\_id value from the SYSIQBACKUPHISTORY table, execute:

```
select * from sysiqbackuphistory
```



<a name="loioa59ba29984f210158062fc278ebdfdba__iq_refbb_1388"/>

## Privileges

Requires EXECUTE object-level privilege on the procedure.



<a name="loioa59ba29984f210158062fc278ebdfdba__section_eh4_db1_nbb"/>

## Side Effects

None



<a name="loioa59ba29984f210158062fc278ebdfdba__iq_refbb_1391"/>

## Example

Sample output from sp\_iqbackupdetails:

```
backup_id   backup_time             backup_type   selective_type   depends_on_id   
      883   2008-09-23 13:58:49.0   Full          All inclusive                0

dbspace_id   dbspace_name   dbspace_rwstatus   dbspace_createid
         0   system         ReadWrite                         0

dbspace_alterid   dbspace_online dbspace_size dbspace_backup_size dbfile_id
              0                0         2884                2884         0

dbfile_name dbfile_rwstatus dbfile_createid dbfile_alterid dbfile_size
     system        ReadWrite                 0               0       2884
```

```
dbfile_backup_size dbfile_path  
             2884  C:\\Documents and Settings\\All Users\\IQ\\demo\\iqdemo.db
```

