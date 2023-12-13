<!-- loioee5019e64a0247cbaf7c8cde5905b3a2 -->

# sp\_delete\_etd\_file System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Deletes specified files from the audit directory in the file container.



<a name="loioee5019e64a0247cbaf7c8cde5905b3a2__section_dh4_3db_1yb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) system procedure can be used when:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.

> ### Restriction:  
> This syntax cannot be run when connected to SAP HANA database as a SAP HANA database user and using SAP HANA database REMOTE\_EXECUTE or REMOTE\_EXECUTE\_QUERY.



```
sp_delete_etd_file( <file-name-pattern> );
```



<a name="loioee5019e64a0247cbaf7c8cde5905b3a2__section_er3_3d2_srb"/>

## Parameters


<dl>
<dt><b>

*<file-name-pattern\>*

</b></dt>
<dd>

Enter a file name pattern for ETD file name matching. Accepts the wildcard characters `*` and `?` .

If null, then deletes all ETD files.



</dd>
</dl>



<a name="loioee5019e64a0247cbaf7c8cde5905b3a2__section_lzx_3d2_srb"/>

## Result Set

None



<a name="loioee5019e64a0247cbaf7c8cde5905b3a2__section_bvg_mx1_1yb"/>

## Privileges



### 

Requires all of the following:

-   EXECUTE object-level privilege on the procedure
-   MANAGE\_AUDITING system privilege



<a name="loioee5019e64a0247cbaf7c8cde5905b3a2__section_j44_jd2_srb"/>

## Side Effects

None



<a name="loioee5019e64a0247cbaf7c8cde5905b3a2__section_s11_kd2_srb"/>

## Examples

Assume you want to delete these three ETD files. Assume you set filename\_prefix to 'my\_session' in the CREATE TEMPORARY TRACE EVENT SESSION statement. The file names start with the string '`my_session_20201126_`':

```
my_session_20201126_181818.173_auditdb_eng.etd 635  2020-09-13 18:40:21.000+00:00
my_session_20201126_184000.000_auditdb_eng.etd 710  2020-11-26 18:50:52.000+00:00
my_session_20201126_185000.000_auditdb_eng.etd  260 2020-11-26 18:50:52.000+00:00
```

Execute:

```
CALL sp_delete_etd_file'my_session_20201126_*';
```

**Related Information**  


[sp\_list\_etd\_files System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)](sp-list-etd-files-system-procedure-for-data-lake-relational-engine-sap-hana-db-managed-0f76c83.md "Lists the event trace data (ETD) files logged to the file container by database auditing.")

[sp_delete_etd_file System Procedure for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/d2e6eeca3f2448159215eead4f812adf.html "Deletes specified files from the audit directory in the file container.") :arrow_upper_right:

