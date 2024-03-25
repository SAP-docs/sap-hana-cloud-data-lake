<!-- loioa59ba29984f210158062fc278ebdfdba -->

# sp\_iqbackupdetails Procedure for Data Lake Relational Engine

Shows all the dbfiles included in a particular backup.



<a name="loioa59ba29984f210158062fc278ebdfdba__section_jjf_yvh_b4b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



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

## Examples

This example uses the sp\_iqbackupdetails system procedure to return information on backup ID 1400410:

```
CALL sp_iqbackupdetails(1400410);
```

Returns:


<table>
<tr>
<th valign="top">

backup\_id

</th>
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

depends\_on\_id

</th>
<th valign="top">

dbspace\_id

</th>
</tr>
<tr>
<td valign="top">

1400410

</td>
<td valign="top">

11:36.0

</td>
<td valign="top">

Virtual cloud

</td>
<td valign="top">

All inclusive

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

1400410

</td>
<td valign="top">

11:36.0

</td>
<td valign="top">

Virtual cloud

</td>
<td valign="top">

All inclusive

</td>
<td valign="top">

0

</td>
<td valign="top">

16384

</td>
</tr>
<tr>
<td valign="top">

1400410

</td>
<td valign="top">

11:36.0

</td>
<td valign="top">

Virtual cloud

</td>
<td valign="top">

All inclusive

</td>
<td valign="top">

0

</td>
<td valign="top">

16387

</td>
</tr>
<tr>
<td valign="top">

1400410

</td>
<td valign="top">

11:36.0

</td>
<td valign="top">

Virtual cloud

</td>
<td valign="top">

All inclusive

</td>
<td valign="top">

0

</td>
<td valign="top">

16388

</td>
</tr>
</table>


<table>
<tr>
<th valign="top" colspan="5">

\(Continued\)

</th>
</tr>
<tr>
<th valign="top">

dbspace\_id

</th>
<th valign="top">

dbspace\_name

</th>
<th valign="top">

dbspace\_rwstatus

</th>
<th valign="top">

dbspace\_createid

</th>
<th valign="top">

dbspace\_alterid

</th>
</tr>
<tr>
<td valign="top">

0

</td>
<td valign="top">

system

</td>
<td valign="top">

ReadWrite

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

16384

</td>
<td valign="top">

IQ\_SYSTEM\_MAIN

</td>
<td valign="top">

ReadWrite

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

16387

</td>
<td valign="top">

hotsql\_dbspace

</td>
<td valign="top">

ReadWrite

</td>
<td valign="top">

20

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

16388

</td>
<td valign="top">

user\_object\_store

</td>
<td valign="top">

ReadWrite

</td>
<td valign="top">

2323

</td>
<td valign="top">

0

</td>
</tr>
</table>


<table>
<tr>
<th valign="top" colspan="5">

\(Continued\)

</th>
</tr>
<tr>
<th valign="top">

dbspace\_online

</th>
<th valign="top">

dbspace\_size

</th>
<th valign="top">

dbspace\_backup\_size

</th>
<th valign="top">

dbfile\_id

</th>
<th valign="top">

dbfile\_name

</th>
</tr>
<tr>
<td valign="top">

Online

</td>
<td valign="top">

5304

</td>
<td valign="top">

5304

</td>
<td valign="top">

0

</td>
<td valign="top">

system

</td>
</tr>
<tr>
<td valign="top">

Online

</td>
<td valign="top">

268435456

</td>
<td valign="top">

21760

</td>
<td valign="top">

16384

</td>
<td valign="top">

IQ\_SYSTEM\_MAIN

</td>
</tr>
<tr>
<td valign="top">

Online

</td>
<td valign="top">

524288

</td>
<td valign="top">

16480

</td>
<td valign="top">

16387

</td>
<td valign="top">

hotsql\_dbspace

</td>
</tr>
<tr>
<td valign="top">

Online

</td>
<td valign="top">

86016

</td>
<td valign="top">

0

</td>
<td valign="top">

16388

</td>
<td valign="top">

user\_object\_store

</td>
</tr>
</table>


<table>
<tr>
<th valign="top" colspan="6">

\(Continued\)

</th>
</tr>
<tr>
<th valign="top">

dbfile\_rwstatus

</th>
<th valign="top">

dbfile\_createid

</th>
<th valign="top">

dbfile\_alterid

</th>
<th valign="top">

dbfile\_size

</th>
<th valign="top">

dbfile\_backup\_size

</th>
<th valign="top">

dbfile\_path

</th>
</tr>
<tr>
<td valign="top">

ReadWrite

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

5304

</td>
<td valign="top">

5304

</td>
<td valign="top">

/data\_shared/coord/iqaas.db

</td>
</tr>
<tr>
<td valign="top">

ReadWrite

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

268435456

</td>
<td valign="top">

21760

</td>
<td valign="top">

/data\_shared/coord/iqcnaas.iq0000

</td>
</tr>
<tr>
<td valign="top">

ReadWrite

</td>
<td valign="top">

20

</td>
<td valign="top">

0

</td>
<td valign="top">

524288

</td>
<td valign="top">

16480

</td>
<td valign="top">

/data\_shared/XXXX/XXXX\_dbspace.iq

</td>
</tr>
<tr>
<td valign="top">

ReadWrite

</td>
<td valign="top">

2323

</td>
<td valign="top">

0

</td>
<td valign="top">

86016

</td>
<td valign="top">

0

</td>
<td valign="top">

hdlfs://83fd5f6c-XxXX-XXxX-XXXX-af61cdfa75bb-cloudnative-0/user\_object\_store

</td>
</tr>
</table>

**Related Information**  


[SYSIQBACKUPCATALOG System View for Data Lake Relational Engine](../070-system-and-monitoring-views/sysiqbackupcatalog-system-view-for-data-lake-relational-engine-67c5105.md "Maintains complete and up-to-date information of all data lake Relational Engine backups.")

