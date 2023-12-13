<!-- loioa5a8f31384f21015acefe93bc2998e90 -->

# sp\_iqfile Procedure for Data Lake Relational Engine

Displays detailed information about each dbfile in a dbspace.



<a name="loioa5a8f31384f21015acefe93bc2998e90__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqfile [ <dbspace-name> ];
```



<a name="loioa5a8f31384f21015acefe93bc2998e90__section_anr_clz_mbb"/>

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

DBSpaceName

</td>
<td valign="top">

The name of the dbspace as defined when the database is created. Dbspace names are always case-insensitive, regardless of the CASE IGNORE or CASE RESPECT specifications.

</td>
</tr>
<tr>
<td valign="top">

DBFileName

</td>
<td valign="top">

The logical file name.

</td>
</tr>
<tr>
<td valign="top">

Path

</td>
<td valign="top">

The location of the physical file or raw partition.

</td>
</tr>
<tr>
<td valign="top">

SegmentType

</td>
<td valign="top">

The type of dbspace:

-   `MAIN`
-   `TEMPORARY`
-   `CACHE`



</td>
</tr>
<tr>
<td valign="top">

RWMode

</td>
<td valign="top">

The mode of the dbspace; always read-write \(RW\).

</td>
</tr>
<tr>
<td valign="top">

Online

</td>
<td valign="top">

-   T – online. This is the online value of both the file's associated dbspace and the file in SYS.ISYSIQDBFILE.
-   F – offline.



</td>
</tr>
<tr>
<td valign="top">

Usage

</td>
<td valign="top">

The percent of dbspace currently in use by this file in the dbspace. When run against a worker node, this column displays NA.

</td>
</tr>
<tr>
<td valign="top">

DBFileSize

</td>
<td valign="top">

The current size of the file or raw partition. For a raw partition, this size value can be less than the physical size.

</td>
</tr>
<tr>
<td valign="top">

Reserve

</td>
<td valign="top">

Reserved space that can be added to this file in the dbspace.

</td>
</tr>
<tr>
<td valign="top">

BlkTypes

</td>
<td valign="top">

The space used by both user data and internal system structures.

</td>
</tr>
<tr>
<td valign="top">

FirstBlk

</td>
<td valign="top">

The first object ID in the dbspace.

</td>
</tr>
<tr>
<td valign="top">

LastBlk

</td>
<td valign="top">

The last object ID in the dbspace.

</td>
</tr>
<tr>
<td valign="top">

OkToDrop

</td>
<td valign="top">

"Y" indicates the file can be dropped; otherwise "N".

</td>
</tr>
</table>



<a name="loioa5a8f31384f21015acefe93bc2998e90__iq_refbb_1572"/>

## Remarks

sp\_iqfile displays the usage, properties, and types of data in each dbfile in a dbspace. You can use this information to determine whether data must be moved, and for data that has been moved, whether the old versions have been deallocated.

The identifiers and block types are:

-   A – Active Version
-   B – Backup Structures
-   C – Checkpoint Log
-   D – Database Identity
-   F – Free List
-   G – Global Free List Manager
-   H – Header Blocks of the Free List
-   I – Index Advice Storage
-   M – Multiplex CM. The multiplex commit identity block \(actually 128 blocks\) exists in all data lake Relational Engine databases, even though it is not used by data lake Relational Engine databases.
-   N – Column Use
-   O – Old Version
-   T – Table Use
-   U – Index Use
-   X – Drop at Checkpoint



<a name="loioa5a8f31384f21015acefe93bc2998e90__iq_refbb_1571"/>

## Privileges

Requires EXECUTE object-level privilege on the procedure, along with the MANAGE ANY DBSPACE system privilege.



## Side Effects

None



<a name="loioa5a8f31384f21015acefe93bc2998e90__iq_refbb_1574"/>

## Examples

The following example displays information about the files in the dbspaces:

```
sp_iqfile;
```

```

sp_iqfile;
DBSpaceName,DBFileName,Path,SegmentType,RWMode,Online,
Usage,DBFileSize,Reserve,StripeSize,BlkTypes,FirstBlk,
LastBlk,OkToDrop,servername,mirrorLogicalFileName,IsDASSharedFile

'IQ_SYSTEM_MAIN','IQ_SYSTEM_MAIN',
'../mpx_configdb.iq','MAIN','RW','T','24','700M','0B','1K',
'1H,17888F,32D,2498A,151O,198X,128M,32C',1,89600,'N',,'(NULL)','F'   
'dbsp1','dbsp1','/lint12dev7/users/user4/machine.lint12dev_local/mpxstore/
  mpx_configdb.iqdb1','MAIN','RW','T','1','50M','0B','1K','1H',
  1045440,1051839,'N',,'(NULL)','F'   
'dbsp2','dbsp2','/lint12dev7/users/user4/machine.lint12dev_local/mpxstore/
  mpx_configdb.iqdb2','MAIN','RW','T','1','50M','0B','1K','1H',
  2090880,2097279,'N',,'(NULL)','F'   
'dbsp3','dbsp3','/lint12dev7/users/user4/machine.lint12dev_local/mpxstore/
  mpx_configdb.iqdb3','MAIN','RW','T','1','50M','0B','1K','1H',
  3136320,3142719,'N',,'(NULL)','F'   
'dbsp4','dbsp4','/lint12dev7/users/user4/machine.lint12dev_local/mpxstore/
  mpx_configdb.iqdb4','MAIN','RW','T','1','50M','0B','1K','1H',
  4181760,4188159,'N',,'(NULL)','F'   
'dbsp5','dbsp5','/lint12dev7/users/user4/machine.lint12dev_local/mpxstore/
  mpx_configdb.iqdb5','MAIN','RW','T','1','50M','0B','1K','1H',
  5227200,5233599,'N',,'(NULL)','F'   
'dbsp6','dbsp6','/lint12dev7/users/user4/machine.lint12dev_local/mpxstore/
  mpx_configdb.iqdb6','MAIN','RW','T','1','50M','0B','1K','1H',
  6272640,6279039,'N',,'(NULL)','F'   
'dbsp7','dbsp71','/lint12dev7/users/user4/machine.lint12dev_local/mpxstore/
  mpx_configdb.iqdb71','MAIN','RW','T','1','200M','0B','1K','1H',
  7318080,7343679,'Y',,'(NULL)','F'   
'dbsp7','dbsp72','/lint12dev7/users/user4/machine.lint12dev_local/mpxstore/
  mpx_configdb.iqdb72','MAIN','RW','T','1','200M','0B','1K','1H',
  8363520,8389119,'Y',,'(NULL)','F'   
'dbsp7','dbsp73','/lint12dev7/users/user4/machine.lint12dev_local/mpxstore/
  mpx_configdb.iqdb73','MAIN','RW','T','1','200M','0B','1K','1H',
  9408960,9434559,'Y',,'(NULL)','F'   
'dbsp8','dbsp81','/lint12dev7/users/user4/machine.lint12dev_local/mpxstore/
  mpx_configdb.iqdb81','MAIN','RW','T','1','20M','0B','1K','1H',
  10454400,10456959,'Y',,'(NULL)','F'   
'dbsp8','dbsp82','/lint12dev7/users/user4/machine.lint12dev_local/mpxstore/
  mpx_configdb.iqdb82','MAIN','RW','T','1','20M','0B','1K','1H'
  ,11499840,11502399,'Y',,'(NULL)','F'   
'dbsp8','dbsp83','/lint12dev7/users/user4/machine.lint12dev_local/mpxstore/
  mpx_configdb.iqdb83','MAIN','RW','T','1','20M','0B','1K','1H',
  12545280,12547839,'Y',,'(NULL)','F'   
'das62H2','dasP62H2','/lint12dev7/users/user4/machine.lint12dev_local/mpxstore/
  das62H2_1.iq','MAIN','RW','T','1','10M','0B','1K','1H',
  13590720,13591999,'Y',
  'user4_1927_nw45780','(NULL)','F'   
'das62H2','dasM62H2','/lint12dev7/users/user4/machine.lint12dev_local/mpxstore/
  das62H2_3.iq','MAIN','RW','T','1','10M','0B','1K','1H',14636160,14637439,'Y',
  'user4_1927_nw55880','dasP62H2','F'   
'das62H2','dasM62H2_11','/lint12dev7/users/user4/machine.lint12dev_local/mpxstore/
  das62H2_33.iq','MAIN','RW','T','1','10M','0B','1K','1H',15681600,15682879,'Y',
  'user4_1927_nw45780','dasP62H2','F'   
'das62H2','dasM62H2_22','/lint12dev7/users/user4/machine.lint12dev_local/mpxstore/
  das62H2_44.iq','MAIN','RW','T','1','10M','0B','1K','1H',16727040,16728319,'Y',
  'user4_1927_nw45780','dasP62H2','F'   
'das62H2','dasP62H_55','/lint12dev7/users/user4/machine.lint12dev_local/mpxstore/
  das62H_55.iq','MAIN','RW','T','1','50M','0B','1K','1H',17772480,17778879,'Y',
  'user4_1927_nw55880','(NULL)','F'   
'das62H2','dasM62H_55','/lint12dev7/users/user4/machine.lint12dev_local/mpxstore/
  das62M_55.iq','MAIN','RW','T','1','50M','0B','1K','1H',18817920,18824319,'Y',
  'user4_1927_nw45780','dasP62H_55','F'   
'sfs_dbs','f1','/shared_disk1/users/user4/dasfmpx/nw35095/
  f1.iq','MAIN','RW','T','1','7.81M','0B','1K','1H',2090880,2091879,'Y',
  'nw35095_dbsrv7915','(NULL)','T'
'sfs_dbs','f1_m','/local_disk1/users/user4/dasfmpx/nw411359/
  f1_m.iq','MAIN','RW','T','1','7.81M','0B','1K','1H',2090880,2091879,'Y',
  'nw411359_dbsrv7915','f1','F'
'sfs_dbs','f2','/shared_disk2/users/user4/dasfmpx/nw35095/
  f2.iq','MAIN','RW','T','1','7.81M','0B','1K','1H',3136320,3137319,'Y',
  'nw35095_dbsrv7915','(NULL)','T'
'sfs_dbs','f2_m','/local_disk2/users/user4/dasfmpx/nw411359/
  f2_m.iq','MAIN','RW','T','1','7.81M','0B','1K','1H',3136320,3137319,'Y',
  'nw411359_dbsrv7915','f2','F'
'IQ_SYSTEM_TEMP','IQ_SYSTEM_TEMP','nc110203mpx_configdb.iqtmp','TEMPORARY',
  'RW','T','1','300M','0B','1K','1H,64F,48A',1,38400,'N',
  'tbucken_1927_nc110203','(NULL)','F'
   
```

