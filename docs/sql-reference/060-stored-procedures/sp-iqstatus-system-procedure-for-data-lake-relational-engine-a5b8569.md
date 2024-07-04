<!-- loioa5b8569b84f210159be8f2c13b8ea3fb -->

# sp\_iqstatus System Procedure for Data Lake Relational Engine

Displays a variety of data lake Relational Engine status information about the current database.



<a name="loioa5b8569b84f210159be8f2c13b8ea3fb__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqstatus
```



<a name="loioa5b8569b84f210159be8f2c13b8ea3fb__section_qq5_pvt_3bc"/>

## Parameters

None



<a name="loioa5b8569b84f210159be8f2c13b8ea3fb__section_s1q_5vt_3bc"/>

## Result Set

See below.



<a name="loioa5b8569b84f210159be8f2c13b8ea3fb__iq_refbb_1779"/>

## Remarks

Shows status information about the current database, including the database name, creation date, page size, number of dbspace segments, block usage, buffer usage, I/O, backup information, and so on.

sp\_iqstatus displays an out-of-space status for main and temporary stores. If a store runs into an out-of-space condition, sp\_iqstatus shows Y in the store’s out-of-space status display value.

sp\_iqspaceused returns a subset of the same information as provided by sp\_iqstatus, but allows the user to return the information in SQL variables to be used in calculations.

To display space that can be reclaimed by dropping connections, use sp\_iqstatus and add the results from the two returned rows:

```
SELECT * FROM sp_iqstatus() where name LIKE '%Versions:%'
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

Requires EXECUTE object-level privilege on this procedure, along with one of the following:

-   MANAGE ANY DBSPACE system privilege
-   MONITOR system privilege



## Side Effects

None.



<a name="loioa5b8569b84f210159be8f2c13b8ea3fb__iq_refbb_1780"/>

## Examples

This example returns status in formation for the database.

```
CALL sp_iqstatus;
```


<table>
<tr>
<th valign="top">

Name

</th>
<th valign="top">

Value

</th>
</tr>
<tr>
<td valign="top">

SAP IQ \(TM\)

</td>
<td valign="top">

Copyright \(c\) 1992-2024 by SAP AG or an SAP affiliate company. All rights reserved.

</td>
</tr>
<tr>
<td valign="top">

Version:

</td>
<td valign="top">

17.1.242.4385/4385/P/sp24.02/Linux/Linux64 - x86\_64 - 3.12.49-11/64bit/2024-04-17 05:33:50

</td>
</tr>
<tr>
<td valign="top">

Time Now:

</td>
<td valign="top">

02:15.0

</td>
</tr>
<tr>
<td valign="top">

Build Time:

</td>
<td valign="top">

\#\#\#\#\#\#\#\#

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

IQ Multiplex Write Server

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

524288/32768blksz/16bpp

</td>
</tr>
<tr>
<td valign="top">

Number of Main DB Files:

</td>
<td valign="top">

3

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

Number of Cache Dbspace Files:

</td>
<td valign="top">

0

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

0

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

DB Blocks: 1-8388608

</td>
<td valign="top">

IQ\_SYSTEM\_MAIN

</td>
</tr>
<tr>
<td valign="top">

DB Blocks: 37663488-37679871

</td>
<td valign="top">

hotsql\_dbspace

</td>
</tr>
<tr>
<td valign="top">

Create Time:

</td>
<td valign="top">

11:15.8

</td>
</tr>
<tr>
<td valign="top">

Update Time:

</td>
<td valign="top">

46:04.6

</td>
</tr>
<tr>
<td valign="top">

Main IQ Buffers:

</td>
<td valign="top">

6184

</td>
</tr>
<tr>
<td valign="top">

Temporary IQ Buffers:

</td>
<td valign="top">

6184

</td>
</tr>
<tr>
<td valign="top">

LOAD IQ Buffers:

</td>
<td valign="top">

256

</td>
</tr>
<tr>
<td valign="top">

Main IQ Blocks Used:

</td>
<td valign="top">

NA

</td>
</tr>
<tr>
<td valign="top">

Cache Dbspace IQ Blocks Used:

</td>
<td valign="top">

0 of 0

</td>
</tr>
<tr>
<td valign="top">

Shared Temporary IQ Blocks Used:

</td>
<td valign="top">

NA

</td>
</tr>
<tr>
<td valign="top">

Local Temporary IQ Blocks Used:

</td>
<td valign="top">

177 of 14598144

</td>
</tr>
<tr>
<td valign="top">

Main Reserved Blocks Available:

</td>
<td valign="top">

NA

</td>
</tr>
<tr>
<td valign="top">

Shared Temporary Reserved Blocks Available:

</td>
<td valign="top">

NA

</td>
</tr>
<tr>
<td valign="top">

Local Temporary Reserved Blocks Available:

</td>
<td valign="top">

147456 of 147456

</td>
</tr>
<tr>
<td valign="top">

IQ Dynamic Memory:

</td>
<td valign="top">

Current: 98mb

</td>
</tr>
<tr>
<td valign="top">

IQ Heap Memory:

</td>
<td valign="top">

Current: 20mb

</td>
</tr>
<tr>
<td valign="top">

Main IQ Buffers:

</td>
<td valign="top">

Used: 511

</td>
</tr>
<tr>
<td valign="top">

Temporary IQ Buffers:

</td>
<td valign="top">

Used: 12

</td>
</tr>
<tr>
<td valign="top">

LOAD IQ Buffers:

</td>
<td valign="top">

Used: 0

</td>
</tr>
<tr>
<td valign="top">

Main IQ I/O:

</td>
<td valign="top">

I: L46915/P511 O: C0/D0/P0 D:0 C:58.8

</td>
</tr>
<tr>
<td valign="top">

Temporary IQ I/O:

</td>
<td valign="top">

I: L1628901/P0 O: C99056/D99708/P658 D:99044 C:100.0

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

NA

</td>
</tr>
<tr>
<td valign="top">

Last Full Backup Time:

</td>
<td valign="top">

NA

</td>
</tr>
<tr>
<td valign="top">

Last Backup ID:

</td>
<td valign="top">

NA

</td>
</tr>
<tr>
<td valign="top">

Last Backup Type:

</td>
<td valign="top">

NA

</td>
</tr>
<tr>
<td valign="top">

Last Backup Time:

</td>
<td valign="top">

NA

</td>
</tr>
<tr>
<td valign="top">

DB Updated:

</td>
<td valign="top">

NA

</td>
</tr>
<tr>
<td valign="top">

Last Full Backup Time:

</td>
<td valign="top">

NA

</td>
</tr>
<tr>
<td valign="top">

Blocks in next ISI Backup:

</td>
<td valign="top">

NA

</td>
</tr>
<tr>
<td valign="top">

Main Tlvlog Size:

</td>
<td valign="top">

Pages: 1

</td>
</tr>
<tr>
<td valign="top">

IQ large memory space:

</td>
<td valign="top">

3097Mb

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

128Mb

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

ON

</td>
</tr>
<tr>
<td valign="top">

RLV Status:

</td>
<td valign="top">

\(For internal user only\)

</td>
</tr>
<tr>
<td valign="top">

RLV memory limit \(mb\):

</td>
<td valign="top">

\(For internal user only\)

</td>
</tr>
<tr>
<td valign="top">

RLV memory used \(bytes\):

</td>
<td valign="top">

\(For internal user only\)

</td>
</tr>
<tr>
<td valign="top">

RLV Log Buffers Allocated:

</td>
<td valign="top">

\(For internal user only\)

</td>
</tr>
<tr>
<td valign="top">

RLV Log Buffers Globally Free:

</td>
<td valign="top">

\(For internal user only\)

</td>
</tr>
<tr>
<td valign="top">

RLV Log Buffers Privately Free:

</td>
<td valign="top">

\(For internal user only\)

</td>
</tr>
<tr>
<td valign="top">

RLV Log Buffers In Use:

</td>
<td valign="top">

\(For internal user only\)

</td>
</tr>
<tr>
<td valign="top">

Result Cache Result Count:

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

Result Cache Size:

</td>
<td valign="top">

0 = 0Mb

</td>
</tr>
<tr>
<td valign="top">

Max Result Cache Size:

</td>
<td valign="top">

1236 = 618Mb

</td>
</tr>
<tr>
<td valign="top">

Max Result Cache Result Size:

</td>
<td valign="top">

123 = 61Mb

</td>
</tr>
</table>

Use the following is a key to understanding the Main IQ I/O and Temporary IQ I/O output codes:

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


[sp\_iqtransaction System Procedure for Data Lake Relational Engine](sp-iqtransaction-system-procedure-for-data-lake-relational-engine-a5bb670.md "Shows information about transactions and versions.")

[sp\_iqversionuse System Procedure for Data Lake Relational Engine](sp-iqversionuse-system-procedure-for-data-lake-relational-engine-a5bd6f9.md "Displays version usage for the data lake Relational Engine main store.")

