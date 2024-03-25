<!-- loioa5b8569b84f210159be8f2c13b8ea3fb -->

# sp\_iqstatus Procedure for Data Lake Relational Engine

Displays a variety of data lake Relational Engine status information about the current database.



<a name="loioa5b8569b84f210159be8f2c13b8ea3fb__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqstatus
```



<a name="loioa5b8569b84f210159be8f2c13b8ea3fb__iq_refbb_1779"/>

## Remarks

Shows status information about the current database, including the database name, creation date, page size, number of dbspace segments, block usage, buffer usage, I/O, backup information, and so on.

sp\_iqstatus displays an out-of-space status for main and temporary stores. If a store runs into an out-of-space condition, sp\_iqstatus shows Y in the store’s out-of-space status display value.

sp\_iqspaceused returns a subset of the same information as provided by sp\_iqstatus, but allows the user to return the information in SQL variables to be used in calculations.

To display space that can be reclaimed by dropping connections, use sp\_iqstatus and add the results from the two returned rows:

```
(DBA)> select * from sp_iqstatus() where name like '%Versions:%'
Execution time: 6.25 seconds
Name                 Value
----------------------------
Other Versions: 2 = 1968Mb
Active Txn Versions: 1 = C:2175Mb/D:2850Mb

(First 2 rows)
```

The above example output shows that one active write transaction created 2175 MB and destroyed 2850 MB of data. The total data consumed in transactions and not yet released is 4818 MB, or 1968 MB + 2850 MB = 4818 MB.

sp\_iqstatus omits blocks that will be deallocated at the next checkpoint. These blocks do however, appear in sp\_iqdbspace output as type X.

This procedure also lists information about the shared data lake Relational Engine store and data lake Relational Engine temporary store. If sp\_iqstatus shows a high percentage of main blocks in use, run sp\_iqversionuse to see which versions are being used and the amount of space that can be recovered by releasing versions.



<a name="loioa5b8569b84f210159be8f2c13b8ea3fb__iq_refbb_1778"/>

## Privileges

Requires EXECUTE object-level privilege on the procedure along with one of the following:

-   MANAGE ANY DBSPACE system privilege
-   MONITOR system privilege



## Side Effects

None



<a name="loioa5b8569b84f210159be8f2c13b8ea3fb__iq_refbb_1780"/>

## Examples

> ### Note:  
> This example includes a sample user dbspace named iq\_main, which may not be present in your own databases.

The following output is from the sp\_iqstatus stored procedure:


<table>
<tr>
<td valign="top">

SAP IQ \(TM\)

</td>
<td valign="top">

Copyright \(c\) 1992–2016 by SAP AG or an SAP affiliate company. All rights reserved.

</td>
</tr>
<tr>
<td valign="top">

Version:

</td>
<td valign="top">

16.1.010.844/10172/P/Mainline/Enterprise Linux64 - x86\_64 - 2.6.18-194.el5/64bit/2016-12-22 02:31:33

</td>
</tr>
<tr>
<td valign="top">

Time Now:

</td>
<td valign="top">

2017-01-18 20:14:57.664

</td>
</tr>
<tr>
<td valign="top">

Build Time:

</td>
<td valign="top">

2016-12-22 02:31:33

</td>
</tr>
<tr>
<td valign="top">

File Format:

</td>
<td valign="top">

23 on 03/18/1999

</td>
</tr>
<tr>
<td valign="top">

Server mode:

</td>
<td valign="top">

IQ Server

</td>
</tr>
<tr>
<td valign="top">

Catalog Format:

</td>
<td valign="top">

2

</td>
</tr>
<tr>
<td valign="top">

Stored Procedure Revision:

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

Page Size:

</td>
<td valign="top">

131072/8192blksz/16bpp

</td>
</tr>
<tr>
<td valign="top">

Number of Main DB Files:

</td>
<td valign="top">

2

</td>
</tr>
<tr>
<td valign="top">

Main Store Out Of Space:

</td>
<td valign="top">

N

</td>
</tr>
<tr>
<td valign="top">

Number of Shared Temp DB Files:

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

Shared Temp Store Out Of Space:

</td>
<td valign="top">

N

</td>
</tr>
<tr>
<td valign="top">

Number of Local Temp DB Files:

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

Local Temp Store Out Of Space:

</td>
<td valign="top">

N

</td>
</tr>
<tr>
<td valign="top">

DB Blocks: 1–12800

</td>
<td valign="top">

IQ\_SYSTEM\_MAIN

</td>
</tr>
<tr>
<td valign="top">

DB Blocks: 1045440–1058239

</td>
<td valign="top">

iq\_main

</td>
</tr>
<tr>
<td valign="top">

Local Temp Blocks: 1–3200

</td>
<td valign="top">

IQ\_SYSTEM\_TEMP

</td>
</tr>
<tr>
<td valign="top">

Create Time:

</td>
<td valign="top">

2017-01-18 19:09:30.231

</td>
</tr>
<tr>
<td valign="top">

Update Time:

</td>
<td valign="top">

2017-01-18 19:09:34.000

</td>
</tr>
<tr>
<td valign="top">

Main IQ Buffers:

</td>
<td valign="top">

509

</td>
</tr>
<tr>
<td valign="top">

Temporary IQ Buffers:

</td>
<td valign="top">

509

</td>
</tr>
<tr>
<td valign="top">

Main IQ Blocks Used:

</td>
<td valign="top">

5944 of 19200

</td>
</tr>
<tr>
<td valign="top">

Shared Temporary IQ Blocks Used:

</td>
<td valign="top">

0 of 0

</td>
</tr>
<tr>
<td valign="top">

Local Temporary IQ Blocks Used:

</td>
<td valign="top">

65 of 1600

</td>
</tr>
<tr>
<td valign="top">

Main Reserved Blocks Available:

</td>
<td valign="top">

6400 of 6400

</td>
</tr>
<tr>
<td valign="top">

Shared Temporary Reserved Blocks Available:

</td>
<td valign="top">

0 of 0

</td>
</tr>
<tr>
<td valign="top">

Local Temporary Reserved Blocks Available:

</td>
<td valign="top">

1600 of 1600

</td>
</tr>
<tr>
<td valign="top">

IQ Dynamic Memory:

</td>
<td valign="top">

Current: 288mb

</td>
</tr>
<tr>
<td valign="top">

IQ Heap Memory:

</td>
<td valign="top">

Current: 150mb

</td>
</tr>
<tr>
<td valign="top">

Main IQ Buffers:

</td>
<td valign="top">

Used: 6

</td>
</tr>
<tr>
<td valign="top">

Temporary IQ Buffers:

</td>
<td valign="top">

Used: 4

</td>
</tr>
<tr>
<td valign="top">

Main IQ I/O:

</td>
<td valign="top">

I: L200/P6 O: C0/D22/P20 D:0 C:100.0

</td>
</tr>
<tr>
<td valign="top">

Temporary IQ I/O:

</td>
<td valign="top">

I: L710/P0 O: C124/D134/P13 D:120 C:100.0

</td>
</tr>
<tr>
<td valign="top">

Other Versions:

</td>
<td valign="top">

0 = 0Mb

</td>
</tr>
<tr>
<td valign="top">

Active Txn Versions:

</td>
<td valign="top">

0 = C:0Mb/D:0Mb

</td>
</tr>
<tr>
<td valign="top">

Last Full Backup ID:

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

Last Full Backup Time:

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Last Backup ID:

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

Last Backup Type:

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

Last Backup Time:

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

DB Updated:

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

Blocks in next ISF Backup:

</td>
<td valign="top">

0 Blocks: =0Mb

</td>
</tr>
<tr>
<td valign="top">

Blocks in next ISI Backup:

</td>
<td valign="top">

0 Blocks: =0Mb

</td>
</tr>
<tr>
<td valign="top">

IQ large memory space:

</td>
<td valign="top">

2048 Mb

</td>
</tr>
<tr>
<td valign="top">

IQ large memory flexible percentage:

</td>
<td valign="top">

50

</td>
</tr>
<tr>
<td valign="top">

IQ large memory flexible used:

</td>
<td valign="top">

0Mb

</td>
</tr>
<tr>
<td valign="top">

IQ large memory inflexible percentage:

</td>
<td valign="top">

90

</td>
</tr>
<tr>
<td valign="top">

IQ large memory inflexible used:

</td>
<td valign="top">

0Mb

</td>
</tr>
<tr>
<td valign="top">

IQ large memory anti-starvation percentage:

</td>
<td valign="top">

50

</td>
</tr>
<tr>
<td valign="top">

DB File Encryption Status:

</td>
<td valign="top">

OFF

</td>
</tr>
</table>

The following is a key to understanding the Main IQ I/O and Temporary IQ I/O output codes:

-   I – Input
-   L – Logical pages read \(“Finds”\)
-   P – Physical pages read
-   O – Output
-   C – Pages created
-   D – Pages dirtied
-   P – Physically written
-   D – Pages destroyed
-   C – Compression ratio

**Related Information**  


[sp\_iqtransaction Procedure for Data Lake Relational Engine](sp-iqtransaction-procedure-for-data-lake-relational-engine-a5bb670.md "Shows information about transactions and versions.")

[sp\_iqversionuse Procedure for Data Lake Relational Engine](sp-iqversionuse-procedure-for-data-lake-relational-engine-a5bd6f9.md "Displays version usage for the data lake Relational Engine main store.")

