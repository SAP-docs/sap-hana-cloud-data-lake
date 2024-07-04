<!-- loio0f76c8361cd84a2b8b35f74382b9265f -->

# sp\_list\_etd\_files System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Lists the event trace data \(ETD\) files logged to the file container by database auditing.



<a name="loio0f76c8361cd84a2b8b35f74382b9265f__section_dh4_3db_1yb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) system procedure can be used when:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.

> ### Restriction:  
> This syntax cannot be run when connected to SAP HANA database as a SAP HANA database user and using SAP HANA database REMOTE\_EXECUTE or REMOTE\_EXECUTE\_QUERY.



```
sp_list_etd_files( [ <file_name_pattern > ] )
```



<a name="loio0f76c8361cd84a2b8b35f74382b9265f__section_hvz_gm2_srb"/>

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



<a name="loio0f76c8361cd84a2b8b35f74382b9265f__section_qcm_hm2_srb"/>

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



<a name="loio0f76c8361cd84a2b8b35f74382b9265f__section_is1_3m2_srb"/>

## Remarks

The result set displays one ETD file per row.



<a name="loio0f76c8361cd84a2b8b35f74382b9265f__section_gzr_tdb_1yb"/>

## Privileges



### 

Requires all of the following:

-   EXECUTE object-level privilege on the procedure
-   MANAGE AUDITING system privilege
-   MANAGE ANY TRACE SESSION system privilege



<a name="loio0f76c8361cd84a2b8b35f74382b9265f__section_tj4_3m2_srb"/>

## Side Effects

None.



<a name="loio0f76c8361cd84a2b8b35f74382b9265f__section_xws_jm2_srb"/>

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


[sp_list_etd_files System Procedure for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/5f0eb4a9f1734b6d9ef6661867578898.html "Lists the event trace data (ETD) files logged to the file container by database auditing.") :arrow_upper_right:

