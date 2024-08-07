<!-- loio812cbb736ce2101490b7fab431caa9ff -->

# AUDIT\_LOG Option for Data Lake Relational Engine

Specifies the type and location of the audit log.



<a name="loio812cbb736ce2101490b7fab431caa9ff__section_fq2_gpq_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loio812cbb736ce2101490b7fab431caa9ff__audit_log_syntax1"/>

## Syntax

```
AUDIT_LOG = 'FILE ( filename_prefix=<path-and-filename>;
   [ flush_on_write = { ON | OFF }; ]
   [ compressed = { ON | OFF } ] )'
```



<a name="loio812cbb736ce2101490b7fab431caa9ff__audit_log_allowed1"/>

## Allowed Values


<dl>
<dt><b>

*<path-and-filename\>*

</b></dt>
<dd>

A log file name prefix with or without a path. All log files have the extension `.etd`. If a full path is not specified, then the directory where the database is located is used as the root directory.



</dd><dt><b>

flush\_on\_write

</b></dt>
<dd>

A Boolean value that controls whether disk buffers are flushed for each event that is logged. The default is ON. When this parameter is turned on, the performance of the database server may be reduced if many trace events are being logged.



</dd><dt><b>

compressed

</b></dt>
<dd>

A Boolean value that controls compression of the log file to conserve disk space. The default is OFF.



</dd>
</dl>



<a name="loio812cbb736ce2101490b7fab431caa9ff__audit_log_default1"/>

## Default

Empty string



<a name="loio812cbb736ce2101490b7fab431caa9ff__audit_log_priv1"/>

## Privileges

Privilege Category: SECURITY



### 

Requires all of:

-   MANAGE AUDITING system privilege
-   SET ANY CUSTOMER SECURITY OPTION system privilege



<a name="loio812cbb736ce2101490b7fab431caa9ff__audit-log-option-scope1"/>

## Scope


<table>
<tr>
<th valign="top">

 

</th>
<th valign="top">

PUBLIC Role

</th>
<th valign="top">

For Current User

</th>
<th valign="top">

For Other Users

</th>
</tr>
<tr>
<td valign="top">

Allowed to set permanently?

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

Allowed to set temporarily?

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
</tr>
</table>



<a name="loio812cbb736ce2101490b7fab431caa9ff__audit_log_remarks1"/>

## Remarks

This option specifies where to write auditing events.

Duplicate target names are not allowed. If FILE is specified twice, then an error is returned.

If the value of audit\_log is invalid, or if any audit log target cannot be started, then an error is returned and the previous value of audit\_log is restored.

If an attempt to log in to the file fails, then audit events may be missing from a FILE target. If a logging failure occurs, then a message appears in the database server messages window to indicate the earliest occurrence of a failure.

For the audit\_log option to work, set the auditing option to On, and also specify which types of information you want to audit by using the sa\_enable\_auditing\_type system procedure.

If a FILE target is specified, then the database uses an internal trace event session named **audit** to log auditing events to the specified file. The internal trace event session cannot be modified by the user. The trace event session used for auditing differs from user trace event sessions in the following ways:

-   The flush\_on\_write parameter is set to ON by default.



## Example

The following statement sets the audit log to an ETD file target with the prefix '`audit_log`'.

```
SET OPTION PUBLIC.audit_log = 'FILE(filename_prefix=my_audit_log; flush_on_write = ON; compressed = OFF)';
```

**Related Information**  


[AUDIT_LOG Option for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/cb45fed1ddb94d34afb66328c1f412d8.html "Specifies the type and location of the audit log.") :arrow_upper_right:

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

