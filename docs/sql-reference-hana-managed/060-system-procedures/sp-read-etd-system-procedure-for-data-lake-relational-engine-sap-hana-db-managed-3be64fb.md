<!-- loio3be64fbd6c5f1014abaea34c00918824 -->

# sp\_read\_etd System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Reads the specified event trace data \(ETD\) file and returns the contents of the file as a set of rows.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) system procedure can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Running Procedures](remote-execute-usage-examples-for-running-procedures-3e7f86d.md) for more information.



```
sp_read_etd(
<filename_pattern>
[,event_names=<event-name>[,...]]
[,host_names=<host-name>[,...]]
[,severity_level=<integer>]
[,record_start=<integer>]
[,record_end=<integer>]
[,timestamp_start=<timestamp-with-timezone>]
[,timestamp_end=<timestamp-with-timezone>]
[,regex ]=<regular-expression>[,...]]
)
```



<a name="loio3be64fbd6c5f1014abaea34c00918824__section_srh_wj2_srb"/>

## Parameters

  *<filename\_pattern\>* 
 :   Enter a file name pattern for ETD file name matching. Accepts the wildcard characters ***\**** and ***?*** .

    This ARRAY of LONG NVARCHAR values specifies the names of the ETD files to be processed. When multiple files are specified, the function aggregates the results from all specified ETD files and returns the entries in ascending order by timestamp.

   *<event\_names\>* 
 :   This LONG NVARCHAR provides a comma-separated list of events for which data will be returned.

   *<host\_names\>* 
 :   This LONG NVARCHAR provides a comma-separated list of hosts that have generated events.

   *<severity\_level\>* 
 :   This LONG NVARCHAR specifies the maximum severity level to retrieve. A NULL returns all severity levels. The severity levels are:


    <table>
    <tr>
    <th valign="top">

    Severity level


    
    </th>
    <th valign="top">

    Value


    
    </th>
    </tr>
    <tr>
    <td valign="top">

    ALWAYS


    
    </td>
    <td valign="top">

    0


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    CRITICAL


    
    </td>
    <td valign="top">

    50


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    ERROR


    
    </td>
    <td valign="top">

    100


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    WARNING


    
    </td>
    <td valign="top">

    150


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    INFORMATION


    
    </td>
    <td valign="top">

    200


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    DEBUG


    
    </td>
    <td valign="top">

    250


    
    </td>
    </tr>
    </table>
    
   *<record\_start\>* 
 :   This UNSIGNED INT identifies the first record number to retrieve. A value of NULL is treated as a 1. The first record number is 1.

   *<record\_end\>* 
 :   Use this UNSIGNED INT to identify the last record number to retrieve. A value of NULL means return all records from the starting record to the last available record.

   *<timestamp\_start\>* 
 :   Use this TIMESTAMP WITH TIME ZONE to identify the starting timestamp.

   *<timestamp\_end\>* 
 :   Use this TIMESTAMP WITH TIME ZONE to identify the ending timestamp.

   *<regex\>* 
 :   Use this LONG NVARCHAR to specify a regular string expression to filter event fields containing string values. The filtering is treated as a logical AND operation. For parameters consisting of comma-separated lists, the filtering is treated as a logical OR operation.

 

<a name="loio3be64fbd6c5f1014abaea34c00918824__section_b5d_xj2_srb"/>

## Result Set

This procedure returns a result set comprised of rows, as follows:


<table>
<tr>
<th valign="top">

Column



</th>
<th valign="top">

Data type



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

timestamp



</td>
<td valign="top">

TIMESTAMP WITH TIME ZONE



</td>
<td valign="top">

The time the event occurred



</td>
</tr>
<tr>
<td valign="top">

pid



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The process ID that generated the event



</td>
</tr>
<tr>
<td valign="top">

tid



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The thread ID that generated the event



</td>
</tr>
<tr>
<td valign="top">

host\_name



</td>
<td valign="top">

LONG NVARCHAR



</td>
<td valign="top">

The host that generated the event



</td>
</tr>
<tr>
<td valign="top">

os



</td>
<td valign="top">

LONG NVARCHAR



</td>
<td valign="top">

The operating system name



</td>
</tr>
<tr>
<td valign="top">

processor



</td>
<td valign="top">

LONG NVARCHAR



</td>
<td valign="top">

The processor type



</td>
</tr>
<tr>
<td valign="top">

severity



</td>
<td valign="top">

LONG NVARCHAR



</td>
<td valign="top">

The severity level of the event



</td>
</tr>
<tr>
<td valign="top">

severity\_number



</td>
<td valign="top">

TINYINT



</td>
<td valign="top">

The severity level number



</td>
</tr>
<tr>
<td valign="top">

event\_name



</td>
<td valign="top">

LONG NVARCHAR



</td>
<td valign="top">

The name of the event



</td>
</tr>
<tr>
<td valign="top">

event\_data



</td>
<td valign="top">

LONG NVARCHAR



</td>
<td valign="top">

An XML document that describes the fields of the event



</td>
</tr>
<tr>
<td valign="top">

record\_id



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

The order that the event appears in the ETD file. The record\_id starts with 0 and is monotonously increasing, with 0 being the first record in the ETD file.



</td>
</tr>
</table>



<a name="loio3be64fbd6c5f1014abaea34c00918824__section_agh_yj2_srb"/>

## Remarks

The format of the *<event\_data\>* XML document is as follows:

```

<?xml version="1.0" encoding="UTF-8"?>
<event_data num_fields="X">
    <field name="Y" type="YY">Z</field>     
     ...
</event_data>
```

X is the number of fields for the event, Y is the field name, YY is the field type, and Z is the data for that field. Valid values for field types are: integer \(for integer sizes\), string, binary, float, and double. Binary data is shown in base64 encoding.



## Privileges

You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



To call the SP\_READ\_ETD system procedure, use the OPENXML operator to retrieve *<event\_data\>* of a single type of event as columns. The following statement returns the timestamp from the SP\_READ\_ETD system procedure and two values \(ID and INFO\) stored in *<event\_data\>* as a single result set:

```
SELECT T1.timestamp, T2.ID, T2.INFO
FROM dbo.sp_read_etd( 'audit_log_20210305_174604.081_auditdb_eng.etd' ), event_names = 'nop' ) AS T1,
     OPENXML ( T1.event_data, '/event_data' )
         WITH ( 
                ID LONG VARCHAR 'field[@name="id"]/text()', 
                INFO LONG VARCHAR 'field[@name="info"]/text()'
               ) AS T2;

```


<table>
<tr>
<th valign="top">

timestamp



</th>
<th valign="top">

ID



</th>
<th valign="top">

INFO



</th>
</tr>
<tr>
<td valign="top">

2020-09-10 14:10:33.089-04:00



</td>
<td valign="top">

1



</td>
<td valign="top">

abc



</td>
</tr>
<tr>
<td valign="top">

2020-09-10 14:10:36.054-04:00



</td>
<td valign="top">

2



</td>
<td valign="top">

def



</td>
</tr>
</table>

Use the OPENXML operator and LIST function to retrieve *<event\_data\>* for various kinds of events in a single column using the following statement:

```
SELECT 
    T1.timestamp, T1.event_name, list( id.FIELD + '=' + id.TEXT ) as data 
FROM dbo.sp_read_etd( 'trace3.etd' ) ) AS T1,
    OPENXML ( T1.event_data, '/event_data/field' )
        WITH ( FIELD LONG VARCHAR '@name', TEXT LONG VARCHAR 'text()' ) AS id,
GROUP BY T1.timestamp, T1.event_name, T1.event_data;

```


<table>
<tr>
<th valign="top">

timestamp



</th>
<th valign="top">

event\_name



</th>
<th valign="top">

data



</th>
</tr>
<tr>
<td valign="top">

2020-09-10 12:10:13.059-04:00



</td>
<td valign="top">

EVENT2



</td>
<td valign="top">

id=1,desc=abc



</td>
</tr>
<tr>
<td valign="top">

2020-09-10 14:10:46.054-04:00



</td>
<td valign="top">

EVENT1



</td>
<td valign="top">

id=2,location=XYZ,other\_information=abc



</td>
</tr>
</table>

Use a regular expression to filter event fields containing string values. The following statement returns all event fields containing the string 'abc' in the event data column:

```
SELECT * 
FROM dbo.sp_read_etd( 'trace1.etd', regex = '.*abc.*' );
```

**Related Information**  


[sp_read_etd System Procedure for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/54317f64bd364214b86e0e6b5aba2300.html "Reads the specified event trace data (ETD) file and returns the contents of the file as a set of rows.") :arrow_upper_right:

