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

None.



<a name="loiod2e6eeca3f2448159215eead4f812adf__sp_delete_etd_file_remarks1"/>

## Remarks

*<file-name-pattern\>* accepts file names only, and doesn’t accept path names. Entering a "/" character or a path name results in an error.

You cannot delete the last active edt file.



<a name="loiod2e6eeca3f2448159215eead4f812adf__sp_delete_etd_file_priv1"/>

## Privileges



### 

Requires all of the following:

-   EXECUTE object-level privilege on this procedure
-   MANAGE AUDITING system privilege
-   MANAGE ANY TRACE SESSION system privilege



<a name="loiod2e6eeca3f2448159215eead4f812adf__sp_delete_etd_file_sideeffects1"/>

## Side Effects

None.



<a name="loiod2e6eeca3f2448159215eead4f812adf__sp_delete_etd_file_example1"/>

## Examples

Assume you have the following three ETD files. Assume you set filename\_prefix to 'my\_audit\_log'.

```
my_audit_log_20240523_191748.050_mpx-writer-0-0.etd
my_audit_log_20240523_191747.520_mpx-coord-0.etd
my_audit_log_20240523_191741.417_mpx-writer-0-0.etd
my_audit_log_20240523_191740.725_mpx-coord-0.etd
my_audit_log_20240524_190814.286_mpx-writer-0-0.etd
my_audit_log_20240524_190813.734_mpx-coord-0.etd

```

This example deletes only the file named my\_audit\_log\_20240523\_191748.050\_mpx-writer-0-0.etd.

```
CALL sp_delete_etd_file ('my_audit_log_20240523_191748.050_mpx-writer-0-0.etd');
```

This example deletes all the files for 20240523, execute:

```
CALL sp_delete_etd_file ('my_audit_log_20240523_*');
```

**Related Information**  


[sp\_list\_etd\_files System Procedure for Data Lake Relational Engine](sp-list-etd-files-system-procedure-for-data-lake-relational-engine-5f0eb4a.md "Lists the event trace data (ETD) files logged to the file container by database auditing.")

[sp_delete_etd_file System Procedure for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/ee5019e64a0247cbaf7c8cde5905b3a2.html "Deletes specified files from the audit directory in the file container.") :arrow_upper_right:

