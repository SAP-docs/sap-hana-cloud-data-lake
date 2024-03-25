<!-- loiob9f214cdab094fc885a1900d77570fff -->

# TEMP\_EXTRACT\_DIRECTORY Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Controls whether a user is allowed to use the data extraction facility. Also controls the directory into which temp extract files are placed, and overrides a directory path specified in the TEMP\_EXTRACT\_NAME*<N\>* option.



<a name="loiob9f214cdab094fc885a1900d77570fff__section_dzz_4jj_kyb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be set when:

-   Connected to SAP HANA database as a SAP HANA database user..
-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loiob9f214cdab094fc885a1900d77570fff__section_z4p_lwh_mrb"/>

## Syntax

```
TEMP_EXTRACT_DIRECTORY = <string_expression>
```



<a name="loiob9f214cdab094fc885a1900d77570fff__section_nvl_mwh_mrb"/>

## Allowed Values

A string defining the directory path. The string can be:


<table>
<tr>
<th valign="top">

*<string\_expression\>* type

</th>
<th valign="top">

Description

</th>
<th valign="top">

Example

</th>
</tr>
<tr>
<td valign="top">

data lake Files storage

</td>
<td valign="top">

The data lake Files container you're extracting to.

</td>
<td valign="top">

hdlfs://analytics

</td>
</tr>
<tr>
<td valign="top">

Azure storage

</td>
<td valign="top">

The Azure container you're extracting to.

</td>
<td valign="top">

bb://mycontainer/myblob

</td>
</tr>
<tr>
<td valign="top">

AWS storage

</td>
<td valign="top">

The S3 bucket you're extracting to.

</td>
<td valign="top">

s3://mybucket/mydata

</td>
</tr>
</table>



<a name="loiob9f214cdab094fc885a1900d77570fff__section_k22_nwh_mrb"/>

## Default

' ' \(the empty string\)



<a name="loiob9f214cdab094fc885a1900d77570fff__section_dt4_f5c_dxb"/>

## Privileges

Privilege Category: SYSTEM



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

-   Requires the SET ANY CUSTOMER SYSTEM OPTION system privilege to set this database option.



</dd>
</dl>



<a name="loiob9f214cdab094fc885a1900d77570fff__section_c2c_qwh_mrb"/>

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



<a name="loiob9f214cdab094fc885a1900d77570fff__section_urk_qwh_mrb"/>

## Remarks

If the TEMP\_EXTRACT\_DIRECTORY option is:

-   Set to a valid directory path, then temp extract files are placed in that directory – overriding a path specified in the TEMP\_EXTRACT\_NAME*<N\>* options.
-   Set to an invalid directory path, then an error occurs: ***Files does not exist File: *<invalid path\>****
-   Blank, then temporary extract files are placed in directories according to their specification in TEMP\_EXTRACT\_NAME*<N\>*.

For example syntax, see [(Deprecated) Unloading Data to the External Object Store Using the Data Extraction Facility](https://help.sap.com/viewer/a8942f1c84f2101594aad09c82c80aea/2024_1_QRC/en-US/a732a39184f21015979f85151aea1b30.html "The data extraction facility is a group of database options that unload data to the external object store.") :arrow_upper_right:.

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[SET\_TEMPORARY\_OPTION Procedure for SAP HANA Database](../080-sap-hana-database-for-data-lake-relational-engine/set-temporary-option-procedure-for-sap-hana-database-abcd703.md "Grant database options temporarily for the current connection only on a data lake Relational Engine relational container.")

[TEMP\_EXTRACT\_NAME<N\> Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)](temp-extract-name-n-option-for-data-lake-relational-engine-sap-hana-db-managed-1f0b3e1.md "Specifies the data lake Filescontainer object file name, or theAzure block blob name, or the Amazon S3 bucket object name you’re extracting to. You must specify the name when extracting data from data lake Relational Engine to cloud storage.")

[Manage Database Options in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2024_1_QRC/en-US/964f12eb2961478b8205f5bfd8ee2ec6.html "Data lake Relational Engine database options are configurable settings that change the way the data lake Relational Engine instance behaves or performs.") :arrow_upper_right:

[TEMP_EXTRACT_DIRECTORY Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/a65cd33584f210159126844d7b32b6a8.html "Controls whether a user is allowed to use the data extraction facility. Also controls the directory into which temp extract files are placed, and overrides a directory path specified in the TEMP_EXTRACT_NAMEN option.") :arrow_upper_right:

