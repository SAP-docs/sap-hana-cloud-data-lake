<!-- loioa5b7d32a84f21015b4c2b681f35bc231 -->

# sp\_iqstatistics System Procedure for Data Lake Relational Engine

Returns serial number, name, description, value, and unit specifier for each available statistic, or a specified statistic.



<a name="loioa5b7d32a84f21015b4c2b681f35bc231__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqstatistics [ <stat_name> ]
```



<a name="loioa5b7d32a84f21015b4c2b681f35bc231__iq_refbb_1770"/>

## Parameter


<dl>
<dt><b>

*<stat\_name\>*

</b></dt>
<dd>

A VARCHAR parameter that specifies the name of a statistic.



</dd>
</dl>



<a name="loioa5b7d32a84f21015b4c2b681f35bc231__iq_refbb_1774"/>

## Result Set


<table>
<tr>
<th valign="top">

Column Name

</th>
<th valign="top">

Data Type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

stat\_num

</td>
<td valign="top">

UNSIGNED INTEGER

</td>
<td valign="top">

Serial number of a statistic

</td>
</tr>
<tr>
<td valign="top">

stat\_name

</td>
<td valign="top">

VARCHAR\(255\)

</td>
<td valign="top">

Name of statistic

</td>
</tr>
<tr>
<td valign="top">

stat\_desc

</td>
<td valign="top">

VARCHAR\(255\)

</td>
<td valign="top">

Description of statistic

</td>
</tr>
<tr>
<td valign="top">

stat\_value

</td>
<td valign="top">

LONG VARCHAR

</td>
<td valign="top">

Value of statistic

</td>
</tr>
<tr>
<td valign="top">

stat\_unit

</td>
<td valign="top">

VARCHAR\(128\)

</td>
<td valign="top">

Unit specifier

</td>
</tr>
</table>

The following statistics may be returned:


<table>
<tr>
<th valign="top">

stat\_num

</th>
<th valign="top">

stat\_name

</th>
<th valign="top">

stat\_desc

</th>
<th valign="top">

stat\_unit

</th>
</tr>
<tr>
<td valign="top">

0

</td>
<td valign="top">

CpuTotalTime

</td>
<td valign="top">

Total CPU time in seconds consumed by the data lake Relational Engine server since last server startup

</td>
<td valign="top">

Second

</td>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

CpuUserTime

</td>
<td valign="top">

CPU user time in seconds consumed by the data lake Relational Engine server since last server startup

</td>
<td valign="top">

Second

</td>
</tr>
<tr>
<td valign="top">

2

</td>
<td valign="top">

CpuSystemTime

</td>
<td valign="top">

CPU system time in seconds consumed by the data lake Relational Engine server since last server startup

</td>
<td valign="top">

Second

</td>
</tr>
<tr>
<td valign="top">

3

</td>
<td valign="top">

ThreadsFree

</td>
<td valign="top">

Number of data lake Relational Engine threads free

</td>
<td valign="top">

N/A

</td>
</tr>
<tr>
<td valign="top">

4

</td>
<td valign="top">

ThreadsInUse

</td>
<td valign="top">

Number of data lake Relational Engine threads in use

</td>
<td valign="top">

N/A

</td>
</tr>
<tr>
<td valign="top">

5

</td>
<td valign="top">

MemoryAllocated

</td>
<td valign="top">

Allocated memory in megabytes

</td>
<td valign="top">

MB

</td>
</tr>
<tr>
<td valign="top">

6

</td>
<td valign="top">

MemoryMaxAllocated

</td>
<td valign="top">

Max allocated memory in megabytes

</td>
<td valign="top">

MB

</td>
</tr>
<tr>
<td valign="top">

7

</td>
<td valign="top">

MainCacheCurrentSize

</td>
<td valign="top">

Main buffer cache current size in megabytes

</td>
<td valign="top">

MB

</td>
</tr>
<tr>
<td valign="top">

8

</td>
<td valign="top">

MainCacheFinds

</td>
<td valign="top">

Main buffer cache total number of lookup requests

</td>
<td valign="top">

N/A

</td>
</tr>
<tr>
<td valign="top">

9

</td>
<td valign="top">

MainCacheHits

</td>
<td valign="top">

Main buffer cache total number of hits

</td>
<td valign="top">

N/A

</td>
</tr>
<tr>
<td valign="top">

10

</td>
<td valign="top">

MainCachePagesPinned

</td>
<td valign="top">

Main buffer cache number of pages pinned

</td>
<td valign="top">

Page

</td>
</tr>
<tr>
<td valign="top">

11

</td>
<td valign="top">

MainCachePagesPinnedPercentage

</td>
<td valign="top">

Percentage of main buffer cache pages pinned

</td>
<td valign="top">

%

</td>
</tr>
<tr>
<td valign="top">

12

</td>
<td valign="top">

MainCachePagesDirtyPercentage

</td>
<td valign="top">

Percentage of main buffer cache pages dirtied

</td>
<td valign="top">

%

</td>
</tr>
<tr>
<td valign="top">

13

</td>
<td valign="top">

MainCachePagesInUsePercentage

</td>
<td valign="top">

Percentage of main buffer cache pages in use

</td>
<td valign="top">

%

</td>
</tr>
<tr>
<td valign="top">

14

</td>
<td valign="top">

TempCacheCurrentSize

</td>
<td valign="top">

Temporary cache current size in megabytes

</td>
<td valign="top">

MB

</td>
</tr>
<tr>
<td valign="top">

15

</td>
<td valign="top">

TempCacheFinds

</td>
<td valign="top">

Temporary cache total number of lookup requests

</td>
<td valign="top">

N/A

</td>
</tr>
<tr>
<td valign="top">

16

</td>
<td valign="top">

TempCacheHits

</td>
<td valign="top">

Temporary cache total number of hits

</td>
<td valign="top">

N/A

</td>
</tr>
<tr>
<td valign="top">

17

</td>
<td valign="top">

TempCachePagesPinned

</td>
<td valign="top">

Temporary cache number of pages pinned

</td>
<td valign="top">

Page

</td>
</tr>
<tr>
<td valign="top">

18

</td>
<td valign="top">

TempCachePagesPinnedPercentage

</td>
<td valign="top">

Percentage of temporary cache pages pinned

</td>
<td valign="top">

%

</td>
</tr>
<tr>
<td valign="top">

19

</td>
<td valign="top">

TempCachePagesDirtyPercentage

</td>
<td valign="top">

Percentage of temporary cache pages dirtied

</td>
<td valign="top">

%

</td>
</tr>
<tr>
<td valign="top">

20

</td>
<td valign="top">

TempCachePagesInUsePercentage

</td>
<td valign="top">

Percentage of temporary cache pages in use

</td>
<td valign="top">

%

</td>
</tr>
<tr>
<td valign="top">

21

</td>
<td valign="top">

MainStoreDiskReads

</td>
<td valign="top">

Number of kilobytes read from main store

</td>
<td valign="top">

KB

</td>
</tr>
<tr>
<td valign="top">

22

</td>
<td valign="top">

MainStoreDiskWrites

</td>
<td valign="top">

Number of kilobytes written to main store

</td>
<td valign="top">

KB

</td>
</tr>
<tr>
<td valign="top">

23

</td>
<td valign="top">

TempStoreDiskReads

</td>
<td valign="top">

Number of kilobytes read from main store

</td>
<td valign="top">

KB

</td>
</tr>
<tr>
<td valign="top">

24

</td>
<td valign="top">

TempStoreDiskWrites

</td>
<td valign="top">

Number of kilobytes written to main store

</td>
<td valign="top">

KB

</td>
</tr>
<tr>
<td valign="top">

25

</td>
<td valign="top">

ConnectionsTotalConnections

</td>
<td valign="top">

Total number of connections since server startup

</td>
<td valign="top">

N/A

</td>
</tr>
<tr>
<td valign="top">

26

</td>
<td valign="top">

ConnectionsTotalDisonnections

</td>
<td valign="top">

Total number of disconnections since server startup

</td>
<td valign="top">

N/A

</td>
</tr>
<tr>
<td valign="top">

27

</td>
<td valign="top">

ConnectionsActive

</td>
<td valign="top">

Number of active connections

</td>
<td valign="top">

N/A

</td>
</tr>
<tr>
<td valign="top">

28

</td>
<td valign="top">

OperationsWaiting

</td>
<td valign="top">

Number of operations waiting for data lake Relational Engine resource governor

</td>
<td valign="top">

N/A

</td>
</tr>
<tr>
<td valign="top">

29

</td>
<td valign="top">

OperationsActive

</td>
<td valign="top">

Number of active concurrent operations admitted by data lake Relational Engine resource governor

</td>
<td valign="top">

N/A

</td>
</tr>
<tr>
<td valign="top">

30

</td>
<td valign="top">

OperationsActiveLoadTableStatements

</td>
<td valign="top">

Number of active LOAD TABLE statements

</td>
<td valign="top">

N/A

</td>
</tr>
</table>



<a name="loioa5b7d32a84f21015b4c2b681f35bc231__iq_refbb_1773"/>

## Remarks

When stat\_name is provided, sp\_iqstatistics returns one row for the given statistic, or zero rows if the name is invalid. When invoked without any parameter, sp\_iqstatistics returns all statistics.



<a name="loioa5b7d32a84f21015b4c2b681f35bc231__iq_refbb_1772"/>

## Privileges

Requires all of the following:

-   EXECUTE object-level privilege on this procedure
-   MANAGE ANY STATISTICS system privilege



## Side Effects

None.



<a name="loioa5b7d32a84f21015b4c2b681f35bc231__iq_refbb_1775"/>

## Examples

This example displays a single statistic, the total CPU time:

```
CALL sp_iqstatistics ('CpuTotalTime');
```

This example returns all statistics where the *<stat\_name\>* begins with MainCache:

```
SELECT * from sp_iqstatistics() WHERE stat_name LIKE 'MainCache%';
```


<table>
<tr>
<th valign="top">

stat\_num

</th>
<th valign="top">

stat\_name

</th>
<th valign="top">

stat\_desc

</th>
<th valign="top">

stat\_value

</th>
<th valign="top">

stat\_unit

</th>
</tr>
<tr>
<td valign="top">

7

</td>
<td valign="top">

MainCacheCurrentSize

</td>
<td valign="top">

Main dbspace current size in megabytes

</td>
<td valign="top">

64

</td>
<td valign="top">

mb

</td>
</tr>
<tr>
<td valign="top">

8

</td>
<td valign="top">

MainCacheFinds

</td>
<td valign="top">

Main dbspace total number of lookup requests

</td>
<td valign="top">

95303

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

9

</td>
<td valign="top">

MainCacheHits

</td>
<td valign="top">

Main dbspace total number of hits

</td>
<td valign="top">

95283

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

10

</td>
<td valign="top">

MainCachePagesPinned

</td>
<td valign="top">

Main dbspace number of pages pinned

</td>
<td valign="top">

0

</td>
<td valign="top">

page

</td>
</tr>
<tr>
<td valign="top">

11

</td>
<td valign="top">

MainCachePagesPinnedPercentage

</td>
<td valign="top">

Percentage of cache dbspace pages pinned

</td>
<td valign="top">

0

</td>
<td valign="top">

%

</td>
</tr>
<tr>
<td valign="top">

12

</td>
<td valign="top">

MainCachePagesDirtyPercentage

</td>
<td valign="top">

Percentage of cache dbspace pages dirtied

</td>
<td valign="top">

0.39

</td>
<td valign="top">

%

</td>
</tr>
<tr>
<td valign="top">

13

</td>
<td valign="top">

MainCachePagesInUsePercentage

</td>
<td valign="top">

Percentage of cache dbspace pages in use

</td>
<td valign="top">

4.44

</td>
<td valign="top">

%

</td>
</tr>
</table>

