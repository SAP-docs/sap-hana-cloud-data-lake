<!-- loioa5cb7cc084f2101597888efc1f59071c -->

# SYSIQBACKUPHISTORYDETAIL System View for Data Lake Relational Engine

This view describes all the dbfile records present in the database at backup time. Each row in this view describes a particular backup operation that finished successfully.



> ### Restriction:  
> This data lake Relational Engine system view can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.


<table>
<tr>
<th valign="top">

Column Name



</th>
<th valign="top">

Column Type



</th>
<th valign="top">

Description.



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

Transaction identifier of the checkpoint of the operation. Backup ID for backup operation.



</td>
</tr>
<tr>
<td valign="top">

dbspace\_id



</td>
<td valign="top">

SMALLINT



</td>
<td valign="top">

The dbspace ID of which this dbfile record is associated.



</td>
</tr>
<tr>
<td valign="top">

dbfile\_id



</td>
<td valign="top">

SMALLINT



</td>
<td valign="top">

The dbfile ID present in dbspace during ongoing backup operation.



</td>
</tr>
<tr>
<td valign="top">

dbspace\_rwstatus



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

dbspace\_createid



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

The transaction ID of the transaction that created the dbspace.



</td>
</tr>
<tr>
<td valign="top">

dbspace\_alterid



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

Transaction ID that marked the dbspace RO. If not marked, then the create ID.



</td>
</tr>
<tr>
<td valign="top">

dbspace\_online



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

dbfile\_rwstatus



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

dbfile\_createid



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

The transaction ID of the transaction that created this dbfile.



</td>
</tr>
<tr>
<td valign="top">

dbfile\_alterid



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

The transaction ID of the transaction that last altered the read-write status of this dbfile.



</td>
</tr>
<tr>
<td valign="top">

is\_backed\_up



</td>
<td valign="top">

CHAR\(1\)



</td>
<td valign="top">

Indicates that the dbfile is backed up in this backup.



</td>
</tr>
<tr>
<td valign="top">

start\_block



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

Start block for the dbfile.



</td>
</tr>
<tr>
<td valign="top">

num\_blocks



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

Total number of blocks in dbfile.



</td>
</tr>
<tr>
<td valign="top">

num\_blocks\_backed\_up



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

Total number of blocks backed up.



</td>
</tr>
<tr>
<td valign="top">

dbspace\_name



</td>
<td valign="top">

CHAR\(128\)



</td>
<td valign="top">

Dbspace name.



</td>
</tr>
<tr>
<td valign="top">

dbfile\_name



</td>
<td valign="top">

CHAR\(128\)



</td>
<td valign="top">

Logical file name of the dbfile.



</td>
</tr>
<tr>
<td valign="top">

dbfile\_path



</td>
<td valign="top">

LONG VARCHAR



</td>
<td valign="top">

Physical path of the file.



</td>
</tr>
</table>



<a name="loioa5cb7cc084f2101597888efc1f59071c__section_n3y_snq_qbb"/>

## Remarks

It presents group information from `ISYSIQBACKUPHISTORYDETAIL` in a readable format. The column constraint for each column is NOT NULL.



<a name="loioa5cb7cc084f2101597888efc1f59071c__section_gzb_qnq_qbb"/>

## Constraints on Underlying System Table

```
Primary key (bu_id, dbfile_id)
```

```
Foreign key (txn_id) references SYS.ISYSBACKUPHISTORY
```

