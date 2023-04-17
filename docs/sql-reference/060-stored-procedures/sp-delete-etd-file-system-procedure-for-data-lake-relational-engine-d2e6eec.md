<!-- loiod2e6eeca3f2448159215eead4f812adf -->

# sp\_delete\_etd\_file System Procedure for Data Lake Relational Engine

Deletes specified files from the audit directory in the file container.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



sp\_delete\_etd\_file\( *<file\_name\_pattern\>*\)



<a name="loiod2e6eeca3f2448159215eead4f812adf__sp_delete_etd_file_parm1"/>

## Parameters

 *<file\_name\_pattern\>*
 :   Enter a file name pattern for ETD file name matching. Accepts the wildcard characters ***\**** and ***?*** .

    If null, then deletes all ETD files.

 

<a name="loiod2e6eeca3f2448159215eead4f812adf__sp_delete_etd_file_remarks1"/>

## Remarks

The *<filename\_pattern\>* accepts file names only, and doesn’t accept path names. Entering a "/" character or a path name results in an error.



<a name="loiod2e6eeca3f2448159215eead4f812adf__section_x1g_44c_zmb"/>

## Privileges

You have the MANAGE\_AUDITING privilege.



<a name="loiod2e6eeca3f2448159215eead4f812adf__sp_delete_etd_file_sideeffects1"/>

## Side Effects

None



<a name="loiod2e6eeca3f2448159215eead4f812adf__sp_delete_etd_file_example1"/>

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


[sp\_list\_etd\_files System Procedure for Data Lake Relational Engine](sp-list-etd-files-system-procedure-for-data-lake-relational-engine-5f0eb4a.md "Lists the event trace data (ETD) files logged to the file container by database auditing.")

[sp_delete_etd_file System Procedure for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/ee5019e64a0247cbaf7c8cde5905b3a2.html "Deletes specified files from the audit directory in the file container.") :arrow_upper_right:

