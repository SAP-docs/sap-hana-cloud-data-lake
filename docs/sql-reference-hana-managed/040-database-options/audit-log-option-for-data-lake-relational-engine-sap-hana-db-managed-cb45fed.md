<!-- loiocb45fed1ddb94d34afb66328c1f412d8 -->

# AUDIT\_LOG Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Specifies the type and location of the audit log.



<a name="loiocb45fed1ddb94d34afb66328c1f412d8__section_dzz_4jj_kyb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be set when:

-   Connected to SAP HANA database as a SAP HANA database user.
-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loiocb45fed1ddb94d34afb66328c1f412d8__section_tlm_jpy_brb"/>

## Syntax

```
AUDIT_LOG = 'FILE ( filename_prefix=<path-and-filename>;
   [ flush_on_write = { ON | OFF }; ]
   [ compressed = { ON | OFF } ] )'
```



<a name="loiocb45fed1ddb94d34afb66328c1f412d8__section_hww_dhy_brb"/>

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



<a name="loiocb45fed1ddb94d34afb66328c1f412d8__section_tjb_hhy_brb"/>

## Default

Empty string



<a name="loiocb45fed1ddb94d34afb66328c1f412d8__section_j31_3yv_cxb"/>

## Privileges

Privilege Category: SECURITY



### 

The privileges required depend on your data lake Relational Engine \(SAP HANA DB-Managed\) connection method:


<dl>
<dt><b>

Connected to SAP HANA database as a SAP HANA database user:

</b></dt>
<dd>

-   To set a database option permanently, use REMOTE\_EXECUTE.

    Requires one of:

    -   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
    -   EXECUTE permission on the SAP HANA database REMOTE\_EXECUTE procedure associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).

    -   See [REMOTE\_EXECUTE Guidance and Examples for Setting Permanent Database Options](remote-execute-guidance-and-examples-for-setting-permanent-database-options-0023bea.md).





</dd><dt><b>

Connected directly to data lake Relational Engine as a data lake Relational Engine user:

</b></dt>
<dd>

Requires all of:

-   MANAGE AUDITING system privilege
-   SET ANY CUSTOMER SECURITY OPTION system privilege



</dd>
</dl>



<a name="loiocb45fed1ddb94d34afb66328c1f412d8__section_dbj_3nb_dxb"/>

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



<a name="loiocb45fed1ddb94d34afb66328c1f412d8__section_ysx_jhy_brb"/>

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


[AUDIT_LOG Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/812cbb736ce2101490b7fab431caa9ff.html "Specifies the type and location of the audit log.") :arrow_upper_right:

[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

