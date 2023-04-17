<!-- loio5f0eb4a9f1734b6d9ef6661867578898 -->

# sp\_list\_etd\_files System Procedure for Data Lake Relational Engine

Lists the event trace data \(ETD\) files logged to the file container by database auditing.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_list_etd_files([ <file_name_pattern > ])
```



<a name="loio5f0eb4a9f1734b6d9ef6661867578898__sp_list_etd_files_parm1"/>

## Parameters

  *<file\_name\_pattern\>* 
 :   Enter a file name pattern for ETD file name matching. Accepts the wildcard characters ***\**** and ***?*** .

    If null, then lists all ETD files.

 

<a name="loio5f0eb4a9f1734b6d9ef6661867578898__sp_list_etd_files_Output1"/>

## Column Definitions for Output


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

file\_name



</td>
<td valign="top">

LONG NVARCHAR



</td>
<td valign="top">

File name of the ETD file.



</td>
</tr>
<tr>
<td valign="top">

file\_size



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

ETD file size in bytes.



</td>
</tr>
<tr>
<td valign="top">

modified\_date\_time



</td>
<td valign="top">

TIMESTAMP WITH TIME ZONE



</td>
<td valign="top">

Time the ETD file was last modified.



</td>
</tr>
</table>



<a name="loio5f0eb4a9f1734b6d9ef6661867578898__sp_list_etd_files_remarks1"/>

## Remarks

The result set displays one ETD file per row.



<a name="loio5f0eb4a9f1734b6d9ef6661867578898__section_ylc_twb_zmb"/>

## Privileges

You have the MANAGE\_AUDITING privilege.



<a name="loio5f0eb4a9f1734b6d9ef6661867578898__sp_list_etd_files_sideeffects1"/>

## Side Effects

None



<a name="loio5f0eb4a9f1734b6d9ef6661867578898__sp_list_etd_files_example1"/>

## Example

Assume you have a SELECT statement listing all ETD files with a file name beginning with the string '`my_session_20201126_`' :

```
SELECT * FROM dbo.sp_list_etd_files('my_session_20201126_*')


```

The example output is:

```
my_session_20201126_181818.173_auditdb_eng.etd 635  2020-09-13 18:40:21.000+00:00
my_session_20201126_184000.000_auditdb_eng.etd 710  2020-11-26 18:50:52.000+00:00
my_session_20201126_185000.000_auditdb_eng.etd  260 2020-11-26 18:50:52.000+00:00

```

**Related Information**  


[sp_list_etd_files System Procedure for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/0f76c8361cd84a2b8b35f74382b9265f.html "Lists the event trace data (ETD) files logged to the file container by database auditing.") :arrow_upper_right:

