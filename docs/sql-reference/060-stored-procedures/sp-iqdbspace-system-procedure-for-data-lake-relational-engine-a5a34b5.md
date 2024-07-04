<!-- loioa5a34b5f84f21015909de16d66c96e8b -->

# sp\_iqdbspace System Procedure for Data Lake Relational Engine

Displays detailed information about each data lake Relational Engine dbspace.



<a name="loioa5a34b5f84f21015909de16d66c96e8b__section_g1g_zvh_b4b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqdbspace [ <dbspace-name> ]
```



<a name="loioa5a34b5f84f21015909de16d66c96e8b__section_nym_brz_mbb"/>

## Parameters


<dl>
<dt><b>

*<dbspace-name\>*

</b></dt>
<dd>

\(Optional\) A parameter that specifies the name of the dbspace.



</dd>
</dl>



<a name="loioa5a34b5f84f21015909de16d66c96e8b__section_sdb_1rz_mbb"/>

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

The name of the dbspace as defined when the database is created. Dbspace names are always case-insensitive, regardless of the CASE IGNORE or CASE RESPECT specification.

</td>
</tr>
<tr>
<td valign="top">

DBSpaceType

</td>
<td valign="top">

The type of the dbspace \(MAIN, SHARED\_TEMP, TEMPORARY, or CACHE\).

</td>
</tr>
<tr>
<td valign="top">

Writable

</td>
<td valign="top">

T \(writable\) or F \(not writable\).

</td>
</tr>
<tr>
<td valign="top">

Online

</td>
<td valign="top">

T \(online\) or F \(offline\).

</td>
</tr>
<tr>
<td valign="top">

Usage

</td>
<td valign="top">

Not used. Dbspaces show "NA" for this value.

</td>
</tr>
<tr>
<td valign="top">

TotalSize

</td>
<td valign="top">

The total size of all files in the dbspace in the units:

-   B \(bytes\)
-   K \(kilobytes\)
-   M \(megabytes\)
-   G \(gigabytes\)
-   T \(terabytes\)
-   P \(petabytes\)

The user\_object\_store dbspace has no size restriction and shows "NA" for this value.

</td>
</tr>
<tr>
<td valign="top">

Reserve

</td>
<td valign="top">

The total reserved space that can be added to all files in the dbspace.

</td>
</tr>
<tr>
<td valign="top">

NumFiles

</td>
<td valign="top">

The number of files in the dbspace.

</td>
</tr>
<tr>
<td valign="top">

NumRWFiles

</td>
<td valign="top">

The number of read-write files in the dbspace.

</td>
</tr>
<tr>
<td valign="top">

StripeSize

</td>
<td valign="top">

Always 1, if disk striping is on.

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

OkToDrop

</td>
<td valign="top">

"Y" indicates the dbspace can be dropped; otherwise "N".

</td>
</tr>
<tr>
<td valign="top">

is\_dbspace\_preallocated

</td>
<td valign="top">

"F" indicates that the NOPREALLOCATE keyword was used in the CREATE DBSPACE statement when creating the dbspace on a cooked \(not raw\) filesystem; otherwise "T" \(the default\).

</td>
</tr>
</table>



<a name="loioa5a34b5f84f21015909de16d66c96e8b__iq_refbb_1508"/>

## Remarks

Use the information from sp\_iqdbspace to determine whether data must be moved, and for data that has been moved, whether the old versions have been deallocated.

The sp\_iqdbspace procedure returns:

Values of the BlkTypes block type identifiers:

-   A – active version
-   B – backup structures
-   C – checkpoint log
-   D – database identity
-   F – free list
-   G – global free list manager
-   H – header blocks of the free list
-   I – index advice storage
-   M – multiplex CM. The multiplex commit identity block \(actually 128 blocks\) exists in all data lake Relational Engine databases, even though it is not used by data lake Relational Engine databases.
-   N – column use
-   O – old version
-   RU – number of blocks used by the commit log
-   T – table use
-   U – index use
-   X – drop at checkpoint



<a name="loioa5a34b5f84f21015909de16d66c96e8b__iq_refbb_1507"/>

## Privileges

Requires all of the following:

-   EXECUTE object-level privilege on this procedure
-   MANAGE ANY DBSPACE system privilege



## Side Effects

None.



<a name="loioa5a34b5f84f21015909de16d66c96e8b__iq_refbb_1510"/>

## Examples

This example returns information about all dbspaces:

```
CALL sp_iqdbspace;
```


<table>
<tr>
<th valign="top">

DBSpace

Name

</th>
<th valign="top">

DBSpace

Type

</th>
<th valign="top">

Writable

</th>
<th valign="top">

Online

</th>
<th valign="top">

Usage

</th>
<th valign="top">

Total

Size

</th>
<th valign="top">

Reserve

</th>
<th valign="top">

Num

RWFiles

</th>
<th valign="top">

Num

Files

</th>
<th valign="top">

Striping

on

</th>
<th valign="top">

Strip

Size

</th>
<th valign="top">

BlkTypes

</th>
<th valign="top">

OkTo

Drop

</th>
<th valign="top">

lsname

</th>
<th valign="top">

is\_

dbspace\_

preallocated

</th>
</tr>
<tr>
<td valign="top">

hotsql\_dbspace

</td>
<td valign="top">

MAIN

</td>
<td valign="top">

T

</td>
<td valign="top">

T

</td>
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

1

</td>
<td valign="top">

1

</td>
<td valign="top">

T

</td>
<td valign="top">

1M

</td>
<td valign="top">

1H

</td>
<td valign="top">

N

</td>
<td valign="top">

NULL

</td>
<td valign="top">

T

</td>
</tr>
<tr>
<td valign="top">

IQ\_SYSTEM\_MAIN

</td>
<td valign="top">

MAIN

</td>
<td valign="top">

T

</td>
<td valign="top">

T

</td>
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

1

</td>
<td valign="top">

1

</td>
<td valign="top">

T

</td>
<td valign="top">

1M

</td>
<td valign="top">

1H,1677696F,32D,129M

</td>
<td valign="top">

N

</td>
<td valign="top">

NULL

</td>
<td valign="top">

T

</td>
</tr>
<tr>
<td valign="top">

IQ\_SYSTEM\_TEMP

</td>
<td valign="top">

TEMPORARY

</td>
<td valign="top">

T

</td>
<td valign="top">

T

</td>
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

1

</td>
<td valign="top">

1

</td>
<td valign="top">

T

</td>
<td valign="top">

1M

</td>
<td valign="top">

1H,160F,32A

</td>
<td valign="top">

N

</td>
<td valign="top">

NULL

</td>
<td valign="top">

T

</td>
</tr>
<tr>
<td valign="top">

user\_object\_store

</td>
<td valign="top">

MAIN

</td>
<td valign="top">

T

</td>
<td valign="top">

T

</td>
<td valign="top">

NA

</td>
<td valign="top">

NA

</td>
<td valign="top">

512K

</td>
<td valign="top">

1

</td>
<td valign="top">

1

</td>
<td valign="top">

F

</td>
<td valign="top">

1M

</td>
<td valign="top">

1H

</td>
<td valign="top">

N

</td>
<td valign="top">

NULL

</td>
<td valign="top">

T

</td>
</tr>
</table>

**Related Information**  


[sp\_iqindexinfo System Procedure for Data Lake Relational Engine](sp-iqindexinfo-system-procedure-for-data-lake-relational-engine-a5ac909.md "Displays the number of blocks (objects) used per index per main dbspace for a given object. If the object resides on several dbspaces, sp_iqindexinfo returns the space used in all dbspaces, as shown in the example.")

[sp\_iqdbspaceinfo System Procedure for Data Lake Relational Engine](sp-iqdbspaceinfo-system-procedure-for-data-lake-relational-engine-a5a3ca6.md "Displays the size of each object and subobject used in the specified table.")

[sp\_iqspaceinfo System Procedure for Data Lake Relational Engine](sp-iqspaceinfo-system-procedure-for-data-lake-relational-engine-a5b6d30.md "Displays the number of blocks (objects) used by each object in the current database and the name of the dbspace in which the object is located.")

