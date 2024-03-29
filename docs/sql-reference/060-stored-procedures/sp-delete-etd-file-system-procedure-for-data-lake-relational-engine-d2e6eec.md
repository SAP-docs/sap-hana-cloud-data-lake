<!-- loiod2e6eeca3f2448159215eead4f812adf -->

# sp\_delete\_etd\_file System Procedure for Data Lake Relational Engine

Deletes specified files from the audit directory in the file container.



<a name="loiod2e6eeca3f2448159215eead4f812adf__section_p4t_vqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_delete_etd_file( <file-name-pattern> )
```



<a name="loiod2e6eeca3f2448159215eead4f812adf__sp_delete_etd_file_parm1"/>

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



<a name="loiod2e6eeca3f2448159215eead4f812adf__sp_delete_etd_file_result1"/>

## Result Set

None



<a name="loiod2e6eeca3f2448159215eead4f812adf__sp_delete_etd_file_remarks1"/>

## Remarks

*<file-name-pattern\>* accepts file names only, and doesn’t accept path names. Entering a "/" character or a path name results in an error.



<a name="loiod2e6eeca3f2448159215eead4f812adf__sp_delete_etd_file_priv1"/>

## Privileges



### 

Requires all of the following:

-   EXECUTE object-level privilege on the procedure
-   MANAGE AUDITING system privilege



<a name="loiod2e6eeca3f2448159215eead4f812adf__sp_delete_etd_file_sideeffects1"/>

## Side Effects

None



<a name="loiod2e6eeca3f2448159215eead4f812adf__sp_delete_etd_file_example1"/>

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


[sp\_list\_etd\_files System Procedure for Data Lake Relational Engine](sp-list-etd-files-system-procedure-for-data-lake-relational-engine-5f0eb4a.md "Lists the event trace data (ETD) files logged to the file container by database auditing.")

[sp_delete_etd_file System Procedure for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/ee5019e64a0247cbaf7c8cde5905b3a2.html "Deletes specified files from the audit directory in the file container.") :arrow_upper_right:

