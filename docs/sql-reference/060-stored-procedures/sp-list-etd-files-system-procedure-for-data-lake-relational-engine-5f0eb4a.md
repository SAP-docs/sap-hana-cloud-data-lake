<!-- loio5f0eb4a9f1734b6d9ef6661867578898 -->

# sp\_list\_etd\_files System Procedure for Data Lake Relational Engine

Lists the event trace data \(ETD\) files logged to the file container by database auditing.



<a name="loio5f0eb4a9f1734b6d9ef6661867578898__section_p4t_vqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_list_etd_files( [ <file_name_pattern > ] )
```



<a name="loio5f0eb4a9f1734b6d9ef6661867578898__sp_list_etd_files_parm1"/>

## Parameters


<dl>
<dt><b>

*<file\_name\_pattern\>* 

</b></dt>
<dd>

Enter a file name pattern for ETD file name matching. Accepts the wildcard characters `*` and `?` .

If null, then lists all ETD files.



</dd>
</dl>



<a name="loio5f0eb4a9f1734b6d9ef6661867578898__sp_list_etd_files_Output1"/>

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



<a name="loio5f0eb4a9f1734b6d9ef6661867578898__sp_list_etd_files_priv1"/>

## Privileges



### 

Requires all of the following:

-   EXECUTE object-level privilege on the procedure
-   MANAGE AUDITING system privilege
-   MANAGE ANY TRACE SESSION system privilege



<a name="loio5f0eb4a9f1734b6d9ef6661867578898__sp_list_etd_files_sideeffects1"/>

## Side Effects

None.



<a name="loio5f0eb4a9f1734b6d9ef6661867578898__sp_list_etd_files_example1"/>

## Examples

This example returns all ETD files fAssume you have a SELECT statement listing all ETD files with a file name beginning with the string '`my_audit_log_`'.

```
CALL sp_list_etd_files('my_audit_log_*');
```


<table>
<tr>
<th valign="top">

file\_name

</th>
<th valign="top">

file\_size

</th>
<th valign="top">

modified\_date\_time

</th>
</tr>
<tr>
<td valign="top">

my\_audit\_log\_20240607\_000002.351\_mpx-writer-0-0.etd

</td>
<td valign="top">

1135648394

</td>
<td valign="top">

2024-06-07 00:00:18.000+00:00

</td>
</tr>
<tr>
<td valign="top">

my\_audit\_log\_20240607\_000001.803\_mpx-coord-0.etd

</td>
<td valign="top">

1279262720

</td>
<td valign="top">

2024-06-07 20:47:11.000+00:00

</td>
</tr>
<tr>
<td valign="top">

my\_audit\_log\_20240606\_000001.391\_mpx-writer-0-0.etd

</td>
<td valign="top">

1267663963

</td>
<td valign="top">

2024-06-07 00:00:04.000+00:00

</td>
</tr>
</table>

**Related Information**  


[sp_list_etd_files System Procedure for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/0f76c8361cd84a2b8b35f74382b9265f.html "Lists the event trace data (ETD) files logged to the file container by database auditing.") :arrow_upper_right:

