<!-- loiob24b81f09e9a442d842dc39630105c9b -->

# CONVERSION\_ERROR Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Controls reporting of data type conversion failures on fetching information from the database.



<a name="loiob24b81f09e9a442d842dc39630105c9b__section_bph_csj_kyb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be set when:

-   Connected to SAP HANA database as a SAP HANA database user.
-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loiob24b81f09e9a442d842dc39630105c9b__section_gnq_czn_hrb"/>

## Syntax

```
CONVERSION_ERROR = { ON | OFF }
```



<a name="loiob24b81f09e9a442d842dc39630105c9b__section_at1_dzn_hrb"/>

## Allowed Values

ON, OFF



<a name="loiob24b81f09e9a442d842dc39630105c9b__section_znq_dzn_hrb"/>

## Default

ON



<a name="loiob24b81f09e9a442d842dc39630105c9b__section_wt1_31w_cxb"/>

## Privileges

Privilege Category: PUBLIC



### 


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



<a name="loiob24b81f09e9a442d842dc39630105c9b__section_srq_4mb_dxb"/>

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



<a name="loiob24b81f09e9a442d842dc39630105c9b__section_gpv_hzn_hrb"/>

## Remarks

This option controls whether data type conversion failures, when data is fetched from the database or inserted into the database, are reported by the database as errors \(CONVERSION\_ERROR set to ON\), or as warnings \(CONVERSION\_ERROR set to OFF\).

When CONVERSION\_ERROR is set to ON, the SQLE\_CONVERSION\_ERROR error is generated.

If the option is set to OFF, the warning SQLE\_CANNOT\_CONVERT is produced. Each thread doing data conversion for a LOAD statement writes at most one warning message to the `.iqmsg` file.

If conversion errors are reported as warnings only, the NULL value is used in place of the value that could not be converted. In Embedded SQL, an indicator variable is set to -2 for the column or columns that cause the error.

> ### Note:  
> Data lake Relational Engine does not silently truncate the conversion result of numeric and date data types to CHAR and VARCHAR. A conversion error is generated when the following data types are converted to a string that is longer than the column width:
> 
> -   TINYINT, SMALLINT, \[UNSIGNED\] \{ INT | INTEGER \}, \[ UNSIGNED \] BIGINT
> -   NUMERIC, DECIMAL
> -   FLOAT, DOUBLE, REAL
> -   DATE, DATETIME, SMALLDATETIME, TIME, TIMESTAMP
> 
> The CONVERSION\_ERROR option controls data lake Relational Engine behavior in cases of conversion error. If you set the CONVERSION\_ERROR option to:
> 
> -   OFF – then data lake Relational Engine inserts a NULL value when possible
> 
> -   ON – then data lake Relational Engine rolls back the insert and logs a conversion error

**Related Information**  


[Manage Database Options in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2024_3_QRC/en-US/964f12eb2961478b8205f5bfd8ee2ec6.html "Data lake Relational Engine database options are configurable settings that change the way the data lake Relational Engine instance behaves or performs.") :arrow_upper_right:

[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[SET\_TEMPORARY\_OPTION Procedure for SAP HANA Database](../080-sap-hana-database-for-data-lake-relational-engine/set-temporary-option-procedure-for-sap-hana-database-abcd703.md "Grant database options temporarily for the current connection only on a data lake Relational Engine relational container.")

[CONVERSION_ERROR Option \[TSQL\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a63018a284f210159f458fb9eec74501.html "Controls reporting of data type conversion failures on fetching information from the database.") :arrow_upper_right:

