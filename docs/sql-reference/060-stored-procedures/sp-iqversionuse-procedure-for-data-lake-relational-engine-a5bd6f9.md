<!-- loioa5bd6f9384f21015a6c5a6fa5a764404 -->

# sp\_iqversionuse Procedure for Data Lake Relational Engine

Displays version usage for the data lake Relational Engine main store.



<a name="loioa5bd6f9384f21015a6c5a6fa5a764404__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqversionuse
```



<a name="loioa5bd6f9384f21015a6c5a6fa5a764404__section_tpm_xxc_yyb"/>

## Parameters

None



<a name="loioa5bd6f9384f21015a6c5a6fa5a764404__section_e5v_b4m_nbb"/>

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

VersionID

</td>
<td valign="top">

In data lake Relational Engine, the VersionID is displayed as zero. For the coordinator node, the VersionID is the same as the TxnID of the active transaction and VersionID is the same as the CmtID of a committed transaction. In worker nodes, the VersionID is the CmtID of the transaction that created the database version on the coordinator. It is used internally by the data lake Relational Engine in-memory catalog and the data lake Relational Engine transaction manager to uniquely identify a database version to all nodes within a database.

</td>
</tr>
<tr>
<td valign="top">

Server

</td>
<td valign="top">

The node to which users of this version are connected.

</td>
</tr>
<tr>
<td valign="top">

IQConnID

</td>
<td valign="top">

The connection ID using this version.

</td>
</tr>
<tr>
<td valign="top">

WasReported

</td>
<td valign="top">

Indicates whether the node has received usage information for this version.

</td>
</tr>
<tr>
<td valign="top">

MinKBRelease

</td>
<td valign="top">

The minimum amount of space returned once this version is no longer in use.

</td>
</tr>
<tr>
<td valign="top">

MaxKBRelease

</td>
<td valign="top">

The maximum amount of space returned once this version is no longer in use.

</td>
</tr>
</table>



<a name="loioa5bd6f9384f21015a6c5a6fa5a764404__iq_refbb_1837"/>

## Remarks

The sp\_iqversionuse system stored procedure helps troubleshoot situations where the database uses excessive storage space because of multiple table versions.

If out-of-space conditions occur or sp\_iqstatus shows a high percentage of main blocks in use on a node, run sp\_iqversionuse to find out which versions are being used and the amount of space that can be recovered by releasing versions.

The procedure produces a row for each user of a version. Run sp\_iqversionuse first on the coordinator to determine which versions should be released and the amount of space in KB to be released when the version is no longer in use. Connection IDs are displayed in the IQConn column for users connected to the coordinator. Version usage from worker nodes is displayed as the worker node name with connection ID 0.

The amount of space is expressed as a range because the actual amount typically depends on which other versions are released. The actual amount of space released can be anywhere between the values of MinKBRelease and MaxKBRelease. The oldest version always has MinKBRelease equal to MaxKBRelease.

WasReported indicates whether version usage information has been sent from the worker node to the coordinator. WasReported is 0 initially on a coordinator for new versions. WasReported changes to 1 once the system replicates version usage information back to the coordinator.

Run sp\_iqversionuse on worker nodes to determine individual connections to worker nodes. Users from other nodes aren't displayed on a worker node.



<a name="loioa5bd6f9384f21015a6c5a6fa5a764404__iq_refbb_1836"/>

## Privileges

Requires EXECUTE object-level privilege on the procedure, along with the MONITOR system privilege.



## Side Effects

None



<a name="loioa5bd6f9384f21015a6c5a6fa5a764404__iq_refbb_1839"/>

## Examples

The following statement displays the version usage for the data lake Relational Engine instance:

```
CALL sp_iqversionuse;
```


<table>
<tr>
<th valign="top">

VersionID

</th>
<th valign="top">

Server

</th>
<th valign="top">

IQConnID

</th>
<th valign="top">

WasReported

</th>
<th valign="top">

MinKBRelease

</th>
<th valign="top">

MaxKBRelease

</th>
</tr>
<tr>
<td valign="top">

5969223

</td>
<td valign="top">

mpx-writer-0-0

</td>
<td valign="top">

311508

</td>
<td valign="top">

1

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

5969223

</td>
<td valign="top">

mpx-writer-0-0

</td>
<td valign="top">

311510

</td>
<td valign="top">

1

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

5969223

</td>
<td valign="top">

mpx-writer-0-0

</td>
<td valign="top">

311514

</td>
<td valign="top">

1

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

5969223

</td>
<td valign="top">

mpx-writer-0-0

</td>
<td valign="top">

311516

</td>
<td valign="top">

1

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

5969605

</td>
<td valign="top">

mpx-writer-0-0

</td>
<td valign="top">

311704

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
</tr>
</table>

**Related Information**  


[sp\_iqstatus Procedure for Data Lake Relational Engine](sp-iqstatus-procedure-for-data-lake-relational-engine-a5b8569.md "Displays a variety of data lake Relational Engine status information about the current database.")

[sp\_iqtransaction Procedure for Data Lake Relational Engine](sp-iqtransaction-procedure-for-data-lake-relational-engine-a5bb670.md "Shows information about transactions and versions.")

