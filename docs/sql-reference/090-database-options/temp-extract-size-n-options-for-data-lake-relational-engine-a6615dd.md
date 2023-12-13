<!-- loioa6615dd384f21015ae14fe398b6f6188 -->

# TEMP\_EXTRACT\_SIZE<N\> Options for Data Lake Relational Engine

Specifies the maximum sizes of the corresponding output files used by the data extraction facility.



<a name="loioa6615dd384f21015ae14fe398b6f6188__section_fq2_gpq_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa6615dd384f21015ae14fe398b6f6188__temp_extract_sizen_syntax1"/>

## Syntax

```
TEMP_EXTRACT_SIZEn = <value>;
```



<a name="loioa6615dd384f21015ae14fe398b6f6188__temp_extract_sizen_values1"/>

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



<a name="loioa6615dd384f21015ae14fe398b6f6188__temp_extract_sizen_default1"/>

## Default

0 or NULL



<a name="loioa6615dd384f21015ae14fe398b6f6188__temp_extract_sizen_priv1"/>

## Privileges

Privilege Category: PUBLIC



### 

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa6615dd384f21015ae14fe398b6f6188__temp_extract_sizen_scope1"/>

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



<a name="loioa6615dd384f21015ae14fe398b6f6188__temp_extract_sizen_remarks1"/>

## Remarks

TEMP\_EXTRACT\_SIZE1 through TEMP\_EXTRACT\_SIZE8 are used to specify the maximum sizes of the corresponding output files used by the data extraction facility. TEMP\_EXTRACT\_SIZE1 specifies the maximum size of the output file specified by TEMP\_EXTRACT\_NAME1, TEMP\_EXTRACT\_SIZE2 specifies the maximum size of the output file specified by TEMP\_EXTRACT\_NAME2, and so on.

With large cloud storage, such as JFS2, support file size larger than the default value, set TEMP\_EXTRACT\_SIZEn to the value that cloud storage allows. For example, to support l TB set option:

```
TEMP_EXTRACT_SIZE1 = 1073741824 KB;
```

If you are extracting to a single file or a single named pipe, leave the options TEMP\_EXTRACT\_NAME2 through TEMP\_EXTRACT\_NAME8 and TEMP\_EXTRACT\_SIZE1 through TEMP\_EXTRACT\_SIZE8 at their default values.

The TEMP\_EXTRACT\_SIZE*<n\>* options are not compatible with TEMP\_EXTRACT\_APPEND. If you try to restrict the size of the extract append output file, data lake Relational Engine reports an error.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[TEMP_EXTRACT_SIZE<N> Options for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/c475f53096e540a9840e2f2e4c584ad4.html "Specifies the maximum sizes of the corresponding output files used by the data extraction facility.") :arrow_upper_right:

[TEMP\_EXTRACT\_NAME<N\> Option for Data Lake Relational Engine](temp-extract-name-n-option-for-data-lake-relational-engine-a65dd19.md "Specifies the data lake Filescontainer object file name, or theAzure block blob name, or the Amazon S3 bucket object name you’re extracting to. You must specify the name when extracting data from data lake Relational Engine to cloud storage.")

