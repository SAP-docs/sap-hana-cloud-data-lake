<!-- loioa6203ded84f21015bc44c8462220d329 -->

# IQ UTILITIES Statement for Data Lake Relational Engine

Starts a cache monitor that collects buffer cache statistics.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
IQ UTILITIES { MAIN | PRIVATE }
    [ INTO ] <table-name>
    { START MONITOR [ '<monitor-options>' ]
    | STOP MONITOR }
```

```
<monitor-options>
    { -summary 
    | { -append | -truncate } -bufalloc 
    | -cache 
    | -cache_by_type 
    | -contention 
    | -debug 
    | -file_suffix <suffix>
    | -io 
    | -interval <seconds> 
    | -threads }...
```



<a name="loioa6203ded84f21015bc44c8462220d329__IQ_Parameters"/>

## Parameters

 START MONITOR
 :   Starts the data lake Relational Engine buffer cache monitor.

  MAIN
 :   Monitors all tables in the main buffer cache of the data lake Relational Engine store.

  PRIVATE
 :   Monitors all tables in the temp buffer cache of the temporary store.

  *<dummy\_table\_name\>*
 :   Can be any data lake Relational Engine base or temporary table. The table name is required for syntactic compatibility with other IQ UTILITIES commands. It is best to have a table that you use only for monitoring.

  monitor\_options *<options\>*
 :   Controls buffer cache monitor output. You can specify more than one, and they must be enclosed with quotation marks. Valid *<options\>* are:


    <table>
    <tr>
    <th valign="top">

    Option Name


    
    </th>
    <th valign="top">

    Description


    
    </th>
    <th valign="top">

    Usage


    
    </th>
    </tr>
    <tr>
    <td valign="top">

    `-summary`


    
    </td>
    <td valign="top">

    Displays summary information for both the main and temp buffer caches. If you do not specify any monitor options, you receive a summary report.


    
    </td>
    <td valign="top">

    monitor\_options -summary


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    `-cache`


    
    </td>
    <td valign="top">

    Displays main or temp buffer cache activity in detail. Critical fields are ***Finds***, ***HR%***, and ***BWaits***.


    
    </td>
    <td valign="top">

    monitor\_options -cache


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    `-cache_by_type`


    
    </td>
    <td valign="top">

    Breaks `-cache` results down by data lake Relational Engine page type. \(An exception is the ***Bwaits*** column, which shows a total only.\) This format is most useful when you need to supply information to Technical Support.


    
    </td>
    <td valign="top">

    monitor\_options -cache\_by\_type


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    `-file_suffix`


    
    </td>
    <td valign="top">

    Creates a monitor output file named <code><i class="varname">&lt;dbname&gt;</i>.<i class="varname">&lt;connid&gt;</i>-<i class="varname">&lt;main_or_temp&gt;</i>-<i class="varname">&lt;suffix&gt;</i></code>. If you do not specify an optional file extension, the file extension defaults to `.iqmon`.


    
    </td>
    <td valign="top">

    monitor\_options -file\_suffix \{extension\}


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    `-io`


    
    </td>
    <td valign="top">

    Displays main or temp \(private\) buffer cache I/O rates and compression ratios during the specified interval. These counters represent all activity for the server; the information is not broken out by device.


    
    </td>
    <td valign="top">

    monitor\_options -io


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    `-bufalloc`


    
    </td>
    <td valign="top">

    Displays information on the main or temp buffer allocator, which reserves space in the buffer cache for objects like sorts, hashes, and bitmaps.


    
    </td>
    <td valign="top">

    monitor\_options -bufalloc


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    `-contention`


    
    </td>
    <td valign="top">

    Displays many key buffer cache and memory manager locks. These lock and mutex counters show the activity within the buffer cache and heap memory and how quickly these locks were resolved. Timeout numbers that exceed 20 percent indicate a problem.


    
    </td>
    <td valign="top">

    monitor\_options -contention


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    `-threads`


    
    </td>
    <td valign="top">

    Displays the processing thread manager counts. Values are server-wide \(it does not matter whether you select this option for main or private\).


    
    </td>
    <td valign="top">

    monitor\_options -threads


    
    </td>
    </tr>
    <tr>
    <td valign="top">

     `-interval` 


    
    </td>
    <td valign="top">

    Specifies the reporting interval in seconds. The default is every 60 seconds. The minimum is every 2 seconds. You can usually get useful results by running the monitor at the default interval during a query or time of day with performance problems. Short intervals may not give meaningful results. Intervals should be proportional to the job time; one minute is generally more than enough.


    
    </td>
    <td valign="top">

    monitor\_options -interval


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    `-append | -truncate`


    
    </td>
    <td valign="top">

    Appends or truncates output to existing output file. Truncate is the default.


    
    </td>
    <td valign="top">

    monitor\_options -append and `monitor_options -truncate`


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    `-debug`


    
    </td>
    <td valign="top">

    Displays all information available to the performance monitor, whether or not there is a standard display mode that covers the same information. -debug is used mainly to supply information to Technical Support.


    
    </td>
    <td valign="top">

    monitor\_options -debug


    
    </td>
    </tr>
    </table>
    
  STOP MONITOR
 :   Similar to START MONITOR, except that you do not need to specify any options:

    -   To simplify monitor use, create a stored procedure to declare the dummy table, specify its output location, and start the monitor.
    -   The interval, with two exceptions, applies to each line of output, not to each page. The exceptions are the -cache\_by\_type and -debug clauses, where a new page begins for each display.

 

<a name="loioa6203ded84f21015bc44c8462220d329__IQ_Usage"/>

## Remarks

Issue separate commands to monitor each buffer cache. Keep each session open while the monitor collects results; a monitor run stops when you close its connection. A connection can run up to a maximum of two monitor runs, one for the main and one for the temp buffer cache.

Either declare a temporary table for use in monitoring, or create a permanent dummy table when you create a new database, before creating any multiplex query servers. These solutions avoid DDL changes, so that data stays up on query servers during production runs.

On UNIX-like operating systems, you can watch monitor output as queries are running.

For example, starting the monitor with this command sends the output to an ASCII file with the name `dbname.conn#-[main|temp]-iqmon`:

```
iq utilities main into monitor_tab 
    start monitor "-cache -interval 2 -file_suffix iqmon"
```

So, for the iqdemo database, the buffer monitor would send the results to `iqdemo.2-main-iqmon`.

The buffer cache monitor writes the results of each run to these logs:

-   `dbname.connection#-main-iqmon //for main buffer cache results` 
-   `dbname.connection#-temp-iqmon //for temp buffer cache results`

The prefix *<dbname.connection\#\>* represents your database name and connection number. If you see more than one connection number and are uncertain which is yours, you can run the catalog stored procedure `sa_conn_info`. This procedure displays the connection number, user ID, and other information for each active connection to the database. The `-file_suffix` clause to change the suffix `iqmon` to a suffix of your choice. Use a text editor to display or print a file. Running the monitor again from the same database and connection number, overwrites the previous results. To save the results of a monitor run, copy the file to another location or use the `-append` option.



<a name="loioa6203ded84f21015bc44c8462220d329__IQ_Permissions"/>

## Privileges

None



<a name="loioa6203ded84f21015bc44c8462220d329__IQ_Standards"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa6203ded84f21015bc44c8462220d329__IQ_Examples"/>

## Examples

The following example starts the buffer cache monitor and record activity for the data lake Relational Engine temp buffer cache:

```
IQ UTILITIES PRIVATE INTO monitor START MONITOR '-cache -interval 20'
```

**Related Information**  




