<!-- loioa975dc54ec404d3a9667cbc0dd8e9e6c -->

# TEMP\_EXTRACT\_VARYING Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Used in conjunction with TEMP\_EXTRACT\_LENGTH\_PREFIX, the TEMP\_EXTRACT\_VARYING option outputs varchar or varbinary column data in a variable-length format in the extracted file. The prefix field specified by TEMP\_EXTRACT\_LENGTH\_PREFIX option holds the length of column data.



<a name="loioa975dc54ec404d3a9667cbc0dd8e9e6c__section_dzz_4jj_kyb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be set when:

-   Connected to SAP HANA database as a SAP HANA database user.
-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa975dc54ec404d3a9667cbc0dd8e9e6c__section_fzx_4b3_mrb"/>

## Syntax

```
TEMP_EXTRACT_VARYING = { ON | OFF }
```



<a name="loioa975dc54ec404d3a9667cbc0dd8e9e6c__section_o5h_pb3_mrb"/>

## Allowed Values

ON, OFF



<a name="loioa975dc54ec404d3a9667cbc0dd8e9e6c__section_zss_pb3_mrb"/>

## Default

OFF



<a name="loioa975dc54ec404d3a9667cbc0dd8e9e6c__section_m1f_c5c_dxb"/>

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



<a name="loioa975dc54ec404d3a9667cbc0dd8e9e6c__section_ums_qb3_mrb"/>

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



<a name="loioa975dc54ec404d3a9667cbc0dd8e9e6c__section_l2h_rb3_mrb"/>

## Remarks

You can only use TEMP\_EXTRACT\_VARYING for varchar and varbinary columns in a binary mode extraction.

When you set TEMP\_EXTRACT\_VARYING to ON, the data field in the extracted file becomes variable length \(with a prefix field\). The data field occupies only the data length in the extracted file, instead of the declared length of the varchar or varbinary column, so that there is no trailing padding.

Use this option with TEMP\_EXTRACT\_LENGTH\_PREFIX to indicate the data length in the extracted file; there is no column delimiter in binary mode extractions.

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[SET\_TEMPORARY\_OPTION Procedure for SAP HANA Database](../080-sap-hana-database-for-data-lake-relational-engine/set-temporary-option-procedure-for-sap-hana-database-abcd703.md "Grant database options temporarily for the current connection only on a data lake Relational Engine relational container.")

[TEMP\_EXTRACT\_LENGTH\_PREFIX Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)](temp-extract-length-prefix-option-for-data-lake-relational-engine-sap-hana-db-managed-7b60971.md "Adds a prefix field of specified length (byte) for a varchar or varbinary column in the generated output file. This PREFIX field in the extract file holds the length of the column data.")

[(Deprecated) Extract Table Data from Data Lake Relational Engine to Azure Blob Storage](https://help.sap.com/viewer/a8942f1c84f2101594aad09c82c80aea/2024_3_QRC/en-US/72f882141a704328a7ff18c7b0b1914e.html "Use data lake Relational Engine TEMP_EXTRACT database options in your extraction query to extract data lake Relational Engine data to one or more block blobs in an Azure storage account container.") :arrow_upper_right:

[(Deprecated) Extract Table Data from Data Lake Relational Engine to an Amazon S3 Bucket](https://help.sap.com/viewer/a8942f1c84f2101594aad09c82c80aea/2024_3_QRC/en-US/5389c53044504f4b9c5865c8f9366ebe.html "Use data lake Relational Engine TEMP_EXTRACT database options in your extraction query to extract data lake Relational Engine data to one or more objects in an Amazon S3 bucket.") :arrow_upper_right:

[Manage Database Options in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2024_3_QRC/en-US/964f12eb2961478b8205f5bfd8ee2ec6.html "Data lake Relational Engine database options are configurable settings that change the way the data lake Relational Engine instance behaves or performs.") :arrow_upper_right:

[TEMP_EXTRACT_VARYING Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/ceb244e0d1974ae5a432814d38640f9d.html "Used in conjunction with TEMP_EXTRACT_LENGTH_PREFIX, the TEMP_EXTRACT_VARYING option outputs varchar or varbinary column data in a variable-length format in the extracted file. The prefix field specified by TEMP_EXTRACT_LENGTH_PREFIX option holds the length of column data.") :arrow_upper_right:

