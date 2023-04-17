<!-- loioa5b8d81e84f21015b1338b8e36993f14 -->

# sp\_iqsysmon Procedure for Data Lake Relational Engine

Monitors multiple components of data lake Relational Engine, including the management of buffer cache, memory, threads, locks, I/O functions, and CPU utilization.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



 Batch Mode Syntax 1
 :   ```
sp_iqsysmon start_monitor
```

  Batch Mode Syntax 2
 :   ```
sp_iqsysmon stop_monitor [, 'section(s)' ]
```

  Syntax 3
 :   ```
sp_iqsysmon '<time-period>' [, 'section(s)' ]
```

 

<a name="loioa5b8d81e84f21015b1338b8e36993f14__iq_refbb_1784"/>

## Batch Mode Parameters

 start\_monitor
 :   Starts monitoring.

  stop\_monitor
 :   Stops monitoring and displays the report.

  *<time-period\>*
 :   The time period for monitoring, in the form HH:MM:SS.

  section\(s\)
 :   \(Optional\) The abbreviation for one or more sections to be shown by sp\_iqsysmon.

    See the [Remarks](sp-iqsysmon-procedure-for-data-lake-relational-engine-a5b8d81.md#loioa5b8d81e84f21015b1338b8e36993f14__IQ_Remarks) section for a complete list of abbreviations.

    If you specify more than one section, separate the section abbreviations using spaces, and enclose the list in single or double quotes. The default is to display all sections.

    For sections related to the data lake Relational Engine main store, you can specify main or temporary store by prefixing the section abbreviation with 'm' or 't', respectively. Without the prefix, both stores are monitored. For example, if you specify 'mbufman', only the data lake Relational Engine main store buffer manager is monitored. If you specify 'mbufman tbufman' or 'bufman', both the main and temporary store buffer managers are monitored.

 

<a name="loioa5b8d81e84f21015b1338b8e36993f14__iq_refbb_1790"/>

## Remarks

> ### Note:  
> sp\_iqsysmon does not support the data lake Relational Engine components Disk I/O and Lock Manager.

sp\_iqsysmon collects the monitor statistics for the period between starting and stopping the monitor or for the time period specified in the *<time-period\>* parameter. At the end of the monitoring period, sp\_iqsysmon displays a list of consolidated statistics.


<table>
<tr>
<th valign="top">

Report Sections or Data Lake Relational Engine Components to be Reported On



</th>
<th valign="top">

Abbreviation to Type



</th>
</tr>
<tr>
<td valign="top">

Buffer allocation



</td>
<td valign="top">

\(main\) – mbufalloc

\(temporary\) – tbufalloc



</td>
</tr>
<tr>
<td valign="top">

Buffer manager



</td>
<td valign="top">

\(main\) – mbufman

\(temporary\) – tbufman



</td>
</tr>
<tr>
<td valign="top">

Buffer pool



</td>
<td valign="top">

\(main\) – mbufpool

\(temporary\) – tbufpool



</td>
</tr>
<tr>
<td valign="top">

Catalog statistics



</td>
<td valign="top">

catalog



</td>
</tr>
<tr>
<td valign="top">

CPU utilization



</td>
<td valign="top">

cpu



</td>
</tr>
<tr>
<td valign="top">

Free list management



</td>
<td valign="top">

\(main\) – mfreelist

\(temporary\) – tfreelist



</td>
</tr>
<tr>
<td valign="top">

Memory management



</td>
<td valign="top">

memory



</td>
</tr>
<tr>
<td valign="top">

Prefetch management



</td>
<td valign="top">

\(main\) – mprefetch

\(temporary\) – tprefetch



</td>
</tr>
<tr>
<td valign="top">

Large Memory Allocator \(LMA\) statistics



</td>
<td valign="top">

lma



</td>
</tr>
<tr>
<td valign="top">

Server context statistics



</td>
<td valign="top">

server



</td>
</tr>
<tr>
<td valign="top">

Thread management



</td>
<td valign="top">

threads



</td>
</tr>
<tr>
<td valign="top">

Transaction management



</td>
<td valign="top">

txn



</td>
</tr>
</table>

The sp\_iqsysmon stored procedure monitors multiple components of data lake Relational Engine, including the management of buffer cache, memory, threads, locks, I/O functions, and CPU utilization.



### Large Memory Allocator \(LMA\) Statistics

Definitions for the STATS-NAME abbreviations displayed in sp\_iqsysmon output for LMA are:


<table>
<tr>
<th valign="top">

STATS-NAME



</th>
<th valign="top">

Definition



</th>
</tr>
<tr>
<td valign="top">

Large Memory Space



</td>
<td valign="top">

Maximum Large Memory configured size \(-iqlm value from params.cfg\).



</td>
</tr>
<tr>
<td valign="top">

Large Memory Max Flexible



</td>
<td valign="top">

Maximum memory granted for flexible operators. Example: Load Engine \(hash sort merge for hash or hash-range partitioned table and hash sort merge cursor\).



</td>
</tr>
<tr>
<td valign="top">

Large Memory Num Flex Allocations



</td>
<td valign="top">

The count of memory chunks allocated as flex memory.



</td>
</tr>
<tr>
<td valign="top">

Large Memory Flexible %



</td>
<td valign="top">

Percentage of large memory used for flexible operators.



</td>
</tr>
<tr>
<td valign="top">

Large Memory Flexible used



</td>
<td valign="top">

This is the total amount of memory allocated to flex users.



</td>
</tr>
<tr>
<td valign="top">

Large Memory Inflexible %



</td>
<td valign="top">

Percentage of large memory used for inflexible operators \(N-bit metadata structures, data buffer of column vector in load \).



</td>
</tr>
<tr>
<td valign="top">

Large Memory Inflexible used



</td>
<td valign="top">

Large memory used by inflexible operators.



</td>
</tr>
<tr>
<td valign="top">

Large Memory Anti-Starvation %



</td>
<td valign="top">

Applies only to flexible operators.



</td>
</tr>
<tr>
<td valign="top">

Large Memory Num Connections



</td>
<td valign="top">

\(Internal use only\)



</td>
</tr>
</table>



<a name="loioa5b8d81e84f21015b1338b8e36993f14__iq_refbb_1783"/>

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

MONITOR



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



<a name="loioa5b8d81e84f21015b1338b8e36993f14__iq_refbb_1793"/>

## Examples



-   Starts the monitor in batch mode and displays all sections for the main and temporary stores:

    ```
    sp_iqsysmon start_monitor
    sp_iqsysmon stop_monitor
    ```

-   Starts the monitor in batch mode and displays the Buffer Manager and Buffer Pool statistics for the main store:

    ```
    sp_iqsysmon start_monitor
    sp_iqsysmon stop_monitor 'mbufman mbufpool'
    ```

-   Prints monitor information after 10 minutes:

    ```
    sp_iqsysmon '00:10:00'
    ```

-   Prints only the Memory Manager section of the sp\_iqsysmon report after 5 minutes:

    ```
    sp_iqsysmon '00:05:00', memory
    ```

-   Starts the monitor, executes two procedures and a query, stops the monitor, then prints only the Buffer Manager section of the report:

    ```
    sp_iqsysmon start_monitor
         go
         execute proc1
         go
         execute proc2
         go
         select sum(total_sales) from titles
         go
         sp_iqsysmon stop_monitor, bufman
         go
    ```

-   Prints only the Main Buffer Manager and Main Buffer Pool sections of the report after 2 minutes:

    ```
    sp_iqsysmon '00:02:00', 'mbufman mbufpool'
    ```

-   Prints only the LMA sections of the report after 5 seconds:

    ```
    sp_iqsysmon '00:00:05', 'lma'
    ```

-   Runs the monitor in batch mode for 10 seconds and displays the consolidated statistics at the end of the time period:

    ```
    sp_iqsysmon '00:00:10', 'mbufpool memory'
    ```

