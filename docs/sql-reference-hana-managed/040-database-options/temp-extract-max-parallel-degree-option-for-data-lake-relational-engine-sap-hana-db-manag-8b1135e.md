<!-- loio8b1135ed7e324674bbfaede1484ce890 -->

# TEMP\_EXTRACT\_MAX\_PARALLEL\_DEGREE Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Sets the maximum parallel degree for the data extraction facility. The TEMP\_EXTRACT\_MAX\_PARALLEL\_DEGREE option limits the maximum number of threads that run in parallel to extract data.



<a name="loio8b1135ed7e324674bbfaede1484ce890__section_dzz_4jj_kyb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be set when:

-   Connected to SAP HANA database as a SAP HANA database user and using the SAP HANA database REMOTE\_EXECUTE procedure.
-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loio8b1135ed7e324674bbfaede1484ce890__section_pv1_qyh_mrb"/>

## Syntax

```
TEMP_EXTRACT_MAX_PARALLEL_DEGREE = <value>;
```



<a name="loio8b1135ed7e324674bbfaede1484ce890__section_g2v_qyh_mrb"/>

## Allowed Values

Any non-negative integer.



<a name="loio8b1135ed7e324674bbfaede1484ce890__section_hmq_ryh_mrb"/>

## Default

64



<a name="loio8b1135ed7e324674bbfaede1484ce890__section_avm_ytc_dxb"/>

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



<a name="loio8b1135ed7e324674bbfaede1484ce890__section_rr4_syh_mrb"/>

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



<a name="loio8b1135ed7e324674bbfaede1484ce890__section_kg4_5yh_mrb"/>

## Remarks

To enable parallel extract, set TEMP\_EXTRACT\_FILE\_PREFIX but not TEMP\_EXTRACT\_NAME1.

For example syntax, see *Extract Data Lake Relational Engine Table Data to Azure Blob Storage* and *Extract Data Lake Relational Engine Table Data to an Amazon S3 Bucket*.

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[SET\_TEMPORARY\_OPTION Procedure for SAP HANA Database](../080-sap-hana-database-for-data-lake-relational-engine/set-temporary-option-procedure-for-sap-hana-database-abcd703.md "Grant database options temporarily for the current connection only on a data lake Relational Engine relational container.")

[TEMP\_EXTRACT\_FILE\_PREFIX Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)](temp-extract-file-prefix-option-for-data-lake-relational-engine-sap-hana-db-managed-af977f3.md "Sets the prefix of file name for the generated output file of the data parallel extraction facility. thread_ID starts from 1. filecount starts from 1 for each thread ID. Thefilecount part increments when the size of the output file reaches the file size limit specified by the TEMP_EXTRACT_SIZE option.")

[TEMP\_EXTRACT\_NAME<N\> Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)](temp-extract-name-n-option-for-data-lake-relational-engine-sap-hana-db-managed-1f0b3e1.md "Specifies the data lake Filescontainer object file name, or theAzure block blob name, or the Amazon S3 bucket object name you’re extracting to. You must specify the name when extracting data from data lake Relational Engine to cloud storage.")

[(Deprecated) Extract Table Data from Data Lake Relational Engine to Azure Blob Storage](https://help.sap.com/viewer/a8942f1c84f2101594aad09c82c80aea/2023_4_QRC/en-US/72f882141a704328a7ff18c7b0b1914e.html "Use data lake Relational Engine TEMP_EXTRACT database options in your extraction query to extract data lake Relational Engine data to one or more block blobs in an Azure storage account container.") :arrow_upper_right:

[(Deprecated) Extract Table Data from Data Lake Relational Engine to an Amazon S3 Bucket](https://help.sap.com/viewer/a8942f1c84f2101594aad09c82c80aea/2023_4_QRC/en-US/5389c53044504f4b9c5865c8f9366ebe.html "Use data lake Relational Engine TEMP_EXTRACT database options in your extraction query to extract data lake Relational Engine data to one or more objects in an Amazon S3 bucket.") :arrow_upper_right:

[Manage Database Options in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2023_4_QRC/en-US/964f12eb2961478b8205f5bfd8ee2ec6.html "Data lake Relational Engine database options are configurable settings that change the way the data lake Relational Engine instance behaves or performs.") :arrow_upper_right:

[TEMP_EXTRACT_MAX_PARALLEL_DEGREE Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/00f65e6745b74f7090225e374f2a80c9.html "Sets the maximum parallel degree for the data extraction facility. The TEMP_EXTRACT_MAX_PARALLEL_DEGREE option limits the maximum number of threads that run in parallel to extract data.") :arrow_upper_right:

