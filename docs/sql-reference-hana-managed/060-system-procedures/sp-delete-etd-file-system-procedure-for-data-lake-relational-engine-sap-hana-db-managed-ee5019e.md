<!-- loioee5019e64a0247cbaf7c8cde5905b3a2 -->

# sp\_delete\_etd\_file System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Deletes specified files from the audit directory in the file container.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) system procedure can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Running Procedures](remote-execute-usage-examples-for-running-procedures-3e7f86d.md) for more information.



sp\_delete\_etd\_file\( *<file\_name\_pattern\>*\)



<a name="loioee5019e64a0247cbaf7c8cde5905b3a2__section_er3_3d2_srb"/>

## Parameters

 *<file\_name\_pattern\>*
 :   Enter a file name pattern for ETD file name matching. Accepts the wildcard characters ***\**** and ***?*** .

    If null, then deletes all ETD files.

 

<a name="loioee5019e64a0247cbaf7c8cde5905b3a2__section_lzx_3d2_srb"/>

## Parameters

 *<file\_name\_pattern\>*
 :   Enter a file name pattern for ETD file name matching. Accepts the wildcard characters ***\**** and ***?*** .

    If null, then deletes all ETD files.

 

<a name="loioee5019e64a0247cbaf7c8cde5905b3a2__section_x1g_44c_zmb"/>

## Privileges

You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loioee5019e64a0247cbaf7c8cde5905b3a2__section_j44_jd2_srb"/>

## Side Effects

None



<a name="loioee5019e64a0247cbaf7c8cde5905b3a2__section_s11_kd2_srb"/>

## Example

Assume you want to delete these three ETD files. Assume you set filename\_prefix to 'my\_session' in the CREATE TEMPORARY TRACE EVENT SESSION statement. The file names start with the string '`my_session_20201126_`':

```
my_session_20201126_181818.173_auditdb_eng.etd 635  2020-09-13 18:40:21.000+00:00
my_session_20201126_184000.000_auditdb_eng.etd 710  2020-11-26 18:50:52.000+00:00
my_session_20201126_185000.000_auditdb_eng.etd  260 2020-11-26 18:50:52.000+00:00
```

Execute:

```
CALL dbo.sp_delete_etd_file'my_session_20201126_*'
```

**Related Information**  


[sp\_list\_etd\_files System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)](sp-list-etd-files-system-procedure-for-data-lake-relational-engine-sap-hana-db-managed-0f76c83.md "Lists the event trace data (ETD) files logged to the file container by database auditing.")

[sp_delete_etd_file System Procedure for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/d2e6eeca3f2448159215eead4f812adf.html "Deletes specified files from the audit directory in the file container.") :arrow_upper_right:

