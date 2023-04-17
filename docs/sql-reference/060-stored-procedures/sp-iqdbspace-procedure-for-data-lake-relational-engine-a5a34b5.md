<!-- loioa5a34b5f84f21015909de16d66c96e8b -->

# sp\_iqdbspace Procedure for Data Lake Relational Engine

Displays detailed information about each data lake Relational Engine dbspace.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqdbspace [ <dbspace-name> ]
```



<a name="loioa5a34b5f84f21015909de16d66c96e8b__section_nym_brz_mbb"/>

## Parameters

 *<dbspace-name\>*
 :   \(Optional\) A parameter that specifies the name of the dbspace.

 

<a name="loioa5a34b5f84f21015909de16d66c96e8b__section_sdb_1rz_mbb"/>

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

The percent of dbspace currently in use by all files in the dbspace.



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

To run this procedure, you need the EXECUTE privilege on the procedure. See [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md). 

You also need:


<table>
<tr>
<th valign="top">

Privilege Name



</th>
<th valign="top">

Privilege Type



</th>
<th valign="top">

Grant Statement



</th>
</tr>
<tr>
<td valign="top">

MANAGE ANY DBSPACE



</td>
<td valign="top">

System privilege



</td>
<td valign="top">

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md)



</td>
</tr>
</table>



## Side Effects

None



<a name="loioa5a34b5f84f21015909de16d66c96e8b__iq_refbb_1510"/>

## Example

Displays information about dbspaces:


<table>
<tr>
<th valign="top">

DBSpaceName



</th>
<th valign="top">

DBSpaceType



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
</tr>
<tr>
<td valign="top">

iq\_main



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

26



</td>
</tr>
<tr>
<td valign="top">

IQ\_SYSTEM\_LOG



</td>
<td valign="top">

PITR



</td>
<td valign="top">

T



</td>
<td valign="top">

T



</td>
<td valign="top">

0



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

22



</td>
</tr>
<tr>
<td valign="top">

IQ\_SYSTEM\_MAIN



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

23



</td>
</tr>
</table>


<table>
<tr>
<th valign="top">

TotalSize



</th>
<th valign="top">

Reserve



</th>
<th valign="top">

NumRWFiles



</th>
<th valign="top">

NumFiles



</th>
<th valign="top">

Stripingon



</th>
</tr>
<tr>
<td valign="top">

100 M



</td>
<td valign="top">

200 M



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
</tr>
<tr>
<td valign="top">

0 B



</td>
<td valign="top">

0 B



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
</tr>
<tr>
<td valign="top">

100 M



</td>
<td valign="top">

200 M



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
</tr>
<tr>
<td valign="top">

25 M



</td>
<td valign="top">

200 M



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
</tr>
<tr>
<td valign="top">

1000 M



</td>
<td valign="top">

0 B



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
</tr>
</table>


<table>
<tr>
<th valign="top">

StripSize



</th>
<th valign="top">

BlkTypes



</th>
<th valign="top">

OkToDrop



</th>
<th valign="top">

lsname



</th>
<th valign="top">

is\_dbspace\_preallocated



</th>
</tr>
<tr>
<td valign="top">

1 K



</td>
<td valign="top">

1H,3254A



</td>
<td valign="top">

N



</td>
<td valign="top">

\(NULL\)



</td>
<td valign="top">

T



</td>
</tr>
<tr>
<td valign="top">

0 B



</td>
<td valign="top">

1H



</td>
<td valign="top">

N



</td>
<td valign="top">

\(NULL\)



</td>
<td valign="top">

T



</td>
</tr>
<tr>
<td valign="top">

1 K



</td>
<td valign="top">

1H,2528F,32D,128M



</td>
<td valign="top">

N



</td>
<td valign="top">

\(NULL\)



</td>
<td valign="top">

T



</td>
</tr>
<tr>
<td valign="top">

1 K



</td>
<td valign="top">

1H,64F,16A



</td>
<td valign="top">

N



</td>
<td valign="top">

\(NULL\)



</td>
<td valign="top">

T



</td>
</tr>
<tr>
<td valign="top">

1 K



</td>
<td valign="top">

1H,20480R,2096RU,1040RC



</td>
<td valign="top">

N



</td>
<td valign="top">

lsname



</td>
<td valign="top">

T



</td>
</tr>
</table>

**Related Information**  


[sp\_iqindexinfo Procedure for Data Lake Relational Engine](sp-iqindexinfo-procedure-for-data-lake-relational-engine-a5ac909.md "Displays the number of blocks (objects) used per index per main dbspace for a given object. If the object resides on several dbspaces, sp_iqindexinfo returns the space used in all dbspaces, as shown in the example.")

[sp\_iqdbspaceinfo Procedure for Data Lake Relational Engine](sp-iqdbspaceinfo-procedure-for-data-lake-relational-engine-a5a3ca6.md "Displays the size of each object and subobject used in the specified table.")

[sp\_iqspaceinfo Procedure for Data Lake Relational Engine](sp-iqspaceinfo-procedure-for-data-lake-relational-engine-a5b6d30.md "Displays the number of blocks (objects) used by each object in the current database and the name of the dbspace in which the object is located.")

