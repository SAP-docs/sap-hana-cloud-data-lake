<!-- loio486458ad1942418e9d70db482284c485 -->

# QUERY\_PLAN\_AS\_HTML Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Generates graphical query plans in HTML format for viewing in a Web browser.



<a name="loio486458ad1942418e9d70db482284c485__section_dzz_4jj_kyb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be set when:

-   Connected to SAP HANA database as a SAP HANA database user and using the SAP HANA database REMOTE\_EXECUTE procedure.
-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loio486458ad1942418e9d70db482284c485__section_xbb_tdt_lrb"/>

## Syntax

```
QUERY_PLAN_AS_HTML = { ON | OFF };
```



<a name="loio486458ad1942418e9d70db482284c485__section_ckk_tdt_lrb"/>

## Allowed Values

ON, OFF



<a name="loio486458ad1942418e9d70db482284c485__section_c1t_tdt_lrb"/>

## Default

OFF



<a name="loio486458ad1942418e9d70db482284c485__section_bmh_4sb_dxb"/>

## Privileges

Privilege Category: PUBLIC



### 

The privileges required depend on your data lake Relational Engine \(SAP HANA DB-Managed\) connection method and whether you are setting the option temporarily or permanently:


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


-   To set a database option temporarily, use the SET\_TEMPORARY\_OPTION procedure, which requires you be a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.

    -   See [SET\_TEMPORARY\_OPTION Procedure for SAP HANA Database](../080-sap-hana-database-for-data-lake-relational-engine/set-temporary-option-procedure-for-sap-hana-database-abcd703.md).





</dd><dt><b>

Connected directly to data lake Relational Engine as a data lake Relational Engine user:

</b></dt>
<dd>

-   Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



</dd>
</dl>



<a name="loio486458ad1942418e9d70db482284c485__section_tw4_5dt_lrb"/>

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

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

Allowed to set temporarily?

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes \(current connection only\)

</td>
<td valign="top">

No

</td>
</tr>
</table>



<a name="loio486458ad1942418e9d70db482284c485__section_uly_vdt_lrb"/>

## Remarks

When you set this option, also set the QUERY\_NAME option for each query, so you know which query is associated with the query plan.

Data lake Relational Engine writes the plans in the same directory as the `.iqmsg` file. Query plan file names follow these conventions: <code><i class="varname">&lt;user-name&gt;</i>_<i class="varname">&lt;query-name&gt;</i>_<i class="varname">&lt;server-type&gt;</i>_<i class="varname">&lt;server-number&gt;</i>_<i class="varname">&lt;YYYYMMDD_HHMMSS&gt;</i>_<i class="varname">&lt;query-number&gt;</i>_<i class="varname">&lt;fragment-number&gt;</i>.html</code>

For example, if the user HDLADMIN sets the temporary option QUERY\_NAME to 'Query\_1123', a file created on November 8, 2012, at exactly 8:30 a.m. is called `HDLADMIN_QUERY_1123_L_0__20121108_083000_4.html`. The date, time, and unique *<query-number\>* appended to the file name ensure that existing files are not overwritten. The *<server-type\>* parameter indicates whether the plan originates from a leader \(L\) or worker \(W\) node. The *<server-number\>* identifies the server where the plan originated when all html files are routed to a single directory.

Worker nodes generate an html file for each fragment executed by the worker, which can result in multiple html files from a single query. These files are identified by *<fragment-number\>*.

> ### Note:  
> If you use this feature, monitor your storagespace usage so you leave enough room for your `.iqmsg` and log files to grow. Enable IQ message log wrapping or message log archiving to avoid filling up your message log file.

QUERY\_PLAN\_AS\_HTML acts independently of the setting for the QUERY\_PLAN option. In other words, if QUERY\_PLAN\_AS\_HTML is ON, you get an HTML format query plan whether or not QUERY\_PLAN is ON.

This feature is supported with newer versions of many commonly used browsers. Some browsers might experience problems with plans generated for very complicated queries.

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[SET\_TEMPORARY\_OPTION Procedure for SAP HANA Database](../080-sap-hana-database-for-data-lake-relational-engine/set-temporary-option-procedure-for-sap-hana-database-abcd703.md "Grant database options temporarily for the current connection only on a data lake Relational Engine relational container.")

[QUERY\_NAME Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)](query-name-option-for-data-lake-relational-engine-sap-hana-db-managed-46c2fe6.md "Gives a name to an executed query in its query plan.")

[Manage Database Options in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2023_4_QRC/en-US/964f12eb2961478b8205f5bfd8ee2ec6.html "Data lake Relational Engine database options are configurable settings that change the way the data lake Relational Engine instance behaves or performs.") :arrow_upper_right:

[QUERY_PLAN_AS_HTML Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/a64e45dd84f21015ac0fcd5c96f8f9af.html "Generates graphical query plans in HTML format for viewing in a Web browser.") :arrow_upper_right:

