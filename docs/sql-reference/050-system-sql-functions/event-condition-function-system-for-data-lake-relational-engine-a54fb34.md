<!-- loioa54fb34184f21015a526eae095389392 -->

# EVENT\_CONDITION Function \[System\] for Data Lake Relational Engine

Specifies when an event handler is triggered.



```
EVENT_CONDITION ( <condition-name> )
```



<a name="loioa54fb34184f21015a526eae095389392__event_condition_parm1"/>

## Parameters

 *<condition-name\>*
 :   The condition triggering the event. The possible values are preset in the database, and are case-insensitive. Each condition is valid only for certain event types.

 
<table>
<tr>
<th valign="top">

Condition Name



</th>
<th valign="top">

Units



</th>
<th valign="top">

Valid for



</th>
<th valign="top">

Comment



</th>
</tr>
<tr>
<td valign="top">

DBFreePercent



</td>
<td valign="top">

N/A



</td>
<td valign="top">

DBDiskSpace



</td>
<td valign="top">

DBDiskSpace shows free space in the system database file \(.db file\), not the IQ store.



</td>
</tr>
<tr>
<td valign="top">

DBFreeSpace



</td>
<td valign="top">

Megabytes



</td>
<td valign="top">

DBDiskSpace



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

DBSize



</td>
<td valign="top">

Megabytes



</td>
<td valign="top">

GrowDB



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

ErrorNumber



</td>
<td valign="top">

N/A



</td>
<td valign="top">

RAISERROR



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

IdleTime



</td>
<td valign="top">

Seconds



</td>
<td valign="top">

ServerIdle



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

Interval



</td>
<td valign="top">

Seconds



</td>
<td valign="top">

All



</td>
<td valign="top">

Time since handler last executed.



</td>
</tr>
<tr>
<td valign="top">

LogFreePercent



</td>
<td valign="top">

N/A



</td>
<td valign="top">

LogDiskSpace



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

LogFreeSpace



</td>
<td valign="top">

Megabytes



</td>
<td valign="top">

LogDiskSpace



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

LogSize



</td>
<td valign="top">

Megabytes



</td>
<td valign="top">

GrowLog



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

RemainingValues



</td>
<td valign="top">

Integer



</td>
<td valign="top">

GlobalAutoincrement



</td>
<td valign="top">

The number of remaining values.



</td>
</tr>
<tr>
<td valign="top">

TempFreePercent



</td>
<td valign="top">

N/A



</td>
<td valign="top">

TempDiskSpace



</td>
<td valign="top">

TempDiskSpace shows free space in the system temporary file \(pointed to by TEMP or IQTMP16 environment variable\), not the IQ temporary store.



</td>
</tr>
<tr>
<td valign="top">

TempFreeSpace



</td>
<td valign="top">

Megabytes



</td>
<td valign="top">

TempDiskSpace



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

TempSize



</td>
<td valign="top">

Megabytes



</td>
<td valign="top">

GrowTemp



</td>
<td valign="top">

 



</td>
</tr>
</table>



<a name="loioa54fb34184f21015a526eae095389392__event_condition_returns1"/>

## Returns

INT



<a name="loioa54fb34184f21015a526eae095389392__event_condition_remarks1"/>

## Remarks

To define an event and its associated handler, use the CREATE EVENT statement.

> ### Note:  
> CIS functional compensation performance considerations apply.



<a name="loioa54fb34184f21015a526eae095389392__event_condition_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa54fb34184f21015a526eae095389392__event_condition_example1"/>

## Example

The following event definition uses the EVENT\_CONDITION function:

```
create event LogNotifier
                    type LogDiskSpace
                    where event_condition( 'LogFreePercent' ) < 50
                    handler
                    begin
                    message 'LogNotifier message'
                    end
```

**Related Information**  


[CREATE EVENT Statement for Data Lake Relational Engine](../080-sql-statements/create-event-statement-for-data-lake-relational-engine-a617091.md "Defines an event and its associated handler for automating predefined actions. Also defines scheduled actions.")

[EVENT\_CONDITION\_NAME Function \[System\] for Data Lake Relational Engine](event-condition-name-function-system-for-data-lake-relational-engine-a550344.md "Can be used to list the possible parameters for EVENT_CONDITION.")

[EVENT\_PARAMETER Function \[System\] for Data Lake Relational Engine](event-parameter-function-system-for-data-lake-relational-engine-a550b30.md "Provides context information for event handlers.")

