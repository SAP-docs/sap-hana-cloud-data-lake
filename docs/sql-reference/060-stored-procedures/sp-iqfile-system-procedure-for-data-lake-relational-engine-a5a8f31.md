<!-- loioa5a8f31384f21015acefe93bc2998e90 -->

# sp\_iqfile System Procedure for Data Lake Relational Engine

Displays detailed information about each dbfile in a dbspace.



<a name="loioa5a8f31384f21015acefe93bc2998e90__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqfile [ <dbspace-name> ]
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

Requires all of the following:

-   EXECUTE object-level privilege on this procedure
-   MANAGE ANY DBSPACE system privilege



## Side Effects

None



<a name="loioa5a8f31384f21015acefe93bc2998e90__iq_refbb_1574"/>

## Examples

This example returns information about dbfiles in the dbspace:

```
CALL sp_iqfile;
```


<table>
<tr>
<th valign="top">

Usage

</th>
<th valign="top">

DBFileSize

</th>
<th valign="top">

Reserve

</th>
<th valign="top">

Stripe

Size

</th>
<th valign="top">

BlkTypes

</th>
<th valign="top">

FirstBlk

</th>
<th valign="top">

LastBlk

</th>
<th valign="top">

OkTo

Drop

</th>
<th valign="top">

servername

</th>
<th valign="top">

mirrorLogical

FileName

</th>
<th valign="top">

IsDAS

SharedFile

</th>
</tr>
<tr>
<td valign="top">

NA

</td>
<td valign="top">

256G

</td>
<td valign="top">

768G

</td>
<td valign="top">

1M

</td>
<td valign="top">

1H,1677696F,32D,128M

</td>
<td valign="top">

1

</td>
<td valign="top">

8388608

</td>
<td valign="top">

N

</td>
<td valign="top">

\(NULL\)

</td>
<td valign="top">

\(NULL\)

</td>
<td valign="top">

F

</td>
</tr>
<tr>
<td valign="top">

NA

</td>
<td valign="top">

512M

</td>
<td valign="top">

0B

</td>
<td valign="top">

1M

</td>
<td valign="top">

1H

</td>
<td valign="top">

37663488

</td>
<td valign="top">

37679871

</td>
<td valign="top">

N

</td>
<td valign="top">

 

</td>
<td valign="top">

\(NULL\)

</td>
<td valign="top">

F

</td>
</tr>
<tr>
<td valign="top">

NA

</td>
<td valign="top">

NA

</td>
<td valign="top">

424K

</td>
<td valign="top">

1M

</td>
<td valign="top">

1H

</td>
<td valign="top">

4611686018427

</td>
<td valign="top">

9223372036854

</td>
<td valign="top">

N

</td>
<td valign="top">

 

</td>
<td valign="top">

\(NULL\)

</td>
<td valign="top">

F

</td>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

450G

</td>
<td valign="top">

0B

</td>
<td valign="top">

1M

</td>
<td valign="top">

1H,160F,48A

</td>
<td valign="top">

1

</td>
<td valign="top">

14745600

</td>
<td valign="top">

N

</td>
<td valign="top">

 

</td>
<td valign="top">

IQNOTEMP

</td>
<td valign="top">

F

</td>
</tr>
</table>

