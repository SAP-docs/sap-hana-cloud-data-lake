<!-- loioc475f53096e540a9840e2f2e4c584ad4 -->

# TEMP\_EXTRACT\_SIZE<N\> Options for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Specifies the maximum sizes of the corresponding output files used by the data extraction facility.



<a name="loioc475f53096e540a9840e2f2e4c584ad4__section_dzz_4jj_kyb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be set when:

-   Connected to SAP HANA database as a SAP HANA database user and using the SAP HANA database REMOTE\_EXECUTE procedure.
-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioc475f53096e540a9840e2f2e4c584ad4__section_lsm_vvg_hxb"/>

## Syntax

```
TEMP_EXTRACT_SIZEn = <value>;
```



<a name="loioc475f53096e540a9840e2f2e4c584ad4__section_sqx_vvg_hxb"/>

## Allowed Values

There are eight options: TEMP\_EXTRACT\_SIZE1 through TEMP\_EXTRACT\_SIZE8.


<table>
<tr>
<th valign="top" rowspan="1">

Device Type

</th>
<th valign="top" rowspan="1">

Size

</th>
</tr>
<tr>
<td valign="top" rowspan="1">

Storage file

</td>
<td valign="top" rowspan="1">

0 – 512 GB

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

Other

</td>
<td valign="top" rowspan="1">

9007199254740992 KB \(8192 petabytes “unlimited”\)

</td>
</tr>
</table>



<a name="loioc475f53096e540a9840e2f2e4c584ad4__section_p23_pfm_2xb"/>

## Default

0 or NULL



<a name="loioc475f53096e540a9840e2f2e4c584ad4__section_aqb_qfm_2xb"/>

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



<a name="loioc475f53096e540a9840e2f2e4c584ad4__section_p13_sfm_2xb"/>

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



<a name="loioc475f53096e540a9840e2f2e4c584ad4__section_i4h_tfm_2xb"/>

## Remarks

TEMP\_EXTRACT\_SIZE1 through TEMP\_EXTRACT\_SIZE8 are used to specify the maximum sizes of the corresponding output files used by the data extraction facility. TEMP\_EXTRACT\_SIZE1 specifies the maximum size of the output file specified by TEMP\_EXTRACT\_NAME1, TEMP\_EXTRACT\_SIZE2 specifies the maximum size of the output file specified by TEMP\_EXTRACT\_NAME2, and so on.

With large cloud storage, such as JFS2, support file size larger than the default value, set TEMP\_EXTRACT\_SIZEn to the value that cloud storage allows. For example, to support l TB set option:

```
TEMP_EXTRACT_SIZE1 = 1073741824 KB;
```

If you are extracting to a single file or a single named pipe, leave the options TEMP\_EXTRACT\_NAME2 through TEMP\_EXTRACT\_NAME8 and TEMP\_EXTRACT\_SIZE1 through TEMP\_EXTRACT\_SIZE8 at their default values.

The TEMP\_EXTRACT\_SIZE*<n\>* options are not compatible with TEMP\_EXTRACT\_APPEND. If you try to restrict the size of the extract append output file, data lake Relational Engine reports an error.

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[SET\_TEMPORARY\_OPTION Procedure for SAP HANA Database](../080-sap-hana-database-for-data-lake-relational-engine/set-temporary-option-procedure-for-sap-hana-database-abcd703.md "Grant database options temporarily for the current connection only on a data lake Relational Engine relational container.")

[TEMP\_EXTRACT\_ACCESS\_KEY\_ID Option \(Deprecated\) for Data Lake Relational Engine \(SAP HANA DB-Managed\)](temp-extract-access-key-id-option-deprecated-for-data-lake-relational-engine-sap-hana-db-22fc37e.md "Supplies the AWS access key. You must specify the access key when extracting data from data lake Relational Engine to an Amazon S3 bucket.")

[TEMP\_EXTRACT\_CONNECTION\_STRING Option \(Deprecated\) for Data Lake Relational Engine \(SAP HANA DB-Managed\)](temp-extract-connection-string-option-deprecated-for-data-lake-relational-engine-sap-hana-102fce6.md "Specifies the connection string of your Azure storage account.")

[TEMP\_EXTRACT\_NAME<N\> Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)](temp-extract-name-n-option-for-data-lake-relational-engine-sap-hana-db-managed-1f0b3e1.md "Specifies the data lake Filescontainer object file name, or theAzure block blob name, or the Amazon S3 bucket object name you’re extracting to. You must specify the name when extracting data from data lake Relational Engine to cloud storage.")

[TEMP\_EXTRACT\_REGION Option \(Deprecated\) for Data Lake Relational Engine \(SAP HANA DB-Managed\)](temp-extract-region-option-deprecated-for-data-lake-relational-engine-sap-hana-db-managed-38858a2.md "Specifies the AWS region where your Amazon S3 bucket resides. You must specify the region when extracting data from the Amazon S3 bucket.")

[TEMP\_EXTRACT\_SECRET\_ACCESS\_KEY Option \(Deprecated\) for Data Lake Relational Engine \(SAP HANA DB-Managed\)](temp-extract-secret-access-key-option-deprecated-for-data-lake-relational-engine-sap-hana-64f7adf.md "Supplies the AWS secret access key. You must specify the secret access key when extracting data from data lake Relational Engine to an Amazon S3 bucket.")

[(Deprecated) Extract Table Data from Data Lake Relational Engine to Azure Blob Storage](https://help.sap.com/viewer/a8942f1c84f2101594aad09c82c80aea/2023_4_QRC/en-US/72f882141a704328a7ff18c7b0b1914e.html "Use data lake Relational Engine TEMP_EXTRACT database options in your extraction query to extract data lake Relational Engine data to one or more block blobs in an Azure storage account container.") :arrow_upper_right:

[(Deprecated) Extract Table Data from Data Lake Relational Engine to an Amazon S3 Bucket](https://help.sap.com/viewer/a8942f1c84f2101594aad09c82c80aea/2023_4_QRC/en-US/5389c53044504f4b9c5865c8f9366ebe.html "Use data lake Relational Engine TEMP_EXTRACT database options in your extraction query to extract data lake Relational Engine data to one or more objects in an Amazon S3 bucket.") :arrow_upper_right:

[Manage Database Options in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2023_4_QRC/en-US/964f12eb2961478b8205f5bfd8ee2ec6.html "Data lake Relational Engine database options are configurable settings that change the way the data lake Relational Engine instance behaves or performs.") :arrow_upper_right:

[TEMP_EXTRACT_SIZE&lt;N&gt; Options for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/a6615dd384f21015ae14fe398b6f6188.html "Specifies the maximum sizes of the corresponding output files used by the data extraction facility.") :arrow_upper_right:

