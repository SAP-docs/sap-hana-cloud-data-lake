<!-- loio22fc37e9ab4341bca333336f8aec3040 -->

# TEMP\_EXTRACT\_ACCESS\_KEY\_ID Option \(Deprecated\) for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Supplies the AWS access key. You must specify the access key when extracting data from data lake Relational Engine to an Amazon S3 bucket.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Setting Database Options](remote-execute-usage-examples-for-setting-database-options-0023bea.md).



<a name="loio22fc37e9ab4341bca333336f8aec3040__section_hfz_5sh_mrb"/>

## Syntax

```
TEMP_EXTRACT_ACCESS_KEY_ID = <string_expression>
```



<a name="loio22fc37e9ab4341bca333336f8aec3040__section_r3k_vsh_mrb"/>

## Allowed Values

Enter the credential key strings as-is. All characters in the AWS access key are valid in data lake Relational Engine and don’t require escape codes.



<a name="loio22fc37e9ab4341bca333336f8aec3040__section_njb_wsh_mrb"/>

## Default

Null.



<a name="loio22fc37e9ab4341bca333336f8aec3040__section_n2p_ttc_dxb"/>

## Privileges

Privilege Category: PUBLIC



### 

You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loio22fc37e9ab4341bca333336f8aec3040__section_cyp_wsh_mrb"/>

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



<a name="loio22fc37e9ab4341bca333336f8aec3040__section_amg_xsh_mrb"/>

## Remarks

Use TEMP\_EXTRACT\_ACCESS\_KEY\_ID along with the options TEMP\_EXTRACT\_SECRET\_ACCESS\_KEY, TEMP\_EXTRACT\_NAME*<N\>*, and TEMP\_EXTRACT\_REGION in your data extraction query.

Applies to Amazon S3 only. Doesn’t apply to Azure Blob storage.

For example syntax, see *Extract Data Lake Relational Engine Table Data to an Amazon S3 Bucket*.

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[TEMP\_EXTRACT\_NAME<N\> Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)](temp-extract-name-n-option-for-data-lake-relational-engine-sap-hana-db-managed-1f0b3e1.md)

[TEMP\_EXTRACT\_REGION Option \(Deprecated\) for Data Lake Relational Engine \(SAP HANA DB-Managed\)](temp-extract-region-option-deprecated-for-data-lake-relational-engine-sap-hana-db-managed-38858a2.md "Specifies the AWS region where your Amazon S3 bucket resides. You must specify the region when extracting data from the Amazon S3 bucket.")

[TEMP\_EXTRACT\_SECRET\_ACCESS\_KEY Option \(Deprecated\) for Data Lake Relational Engine \(SAP HANA DB-Managed\)](temp-extract-secret-access-key-option-deprecated-for-data-lake-relational-engine-sap-hana-64f7adf.md "Supplies the AWS secret access key. You must specify the secret access key when extracting data from data lake Relational Engine to an Amazon S3 bucket.")

[Manage Database Options in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2023_1_QRC/en-US/964f12eb2961478b8205f5bfd8ee2ec6.html "Data lake Relational Engine database options are configurable settings that change the way the data lake Relational Engine database behaves or performs.") :arrow_upper_right:

[TEMP_EXTRACT_ACCESS_KEY_ID Option (Deprecated) for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/924c9f84b1d54194819442a1b03228b1.html "Supplies the AWS access key. You must specify the access key when extracting data from data lake Relational Engine to an Amazon S3 bucket.") :arrow_upper_right:

