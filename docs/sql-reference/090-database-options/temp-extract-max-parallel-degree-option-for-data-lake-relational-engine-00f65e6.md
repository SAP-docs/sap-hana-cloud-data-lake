<!-- loio00f65e6745b74f7090225e374f2a80c9 -->

# TEMP\_EXTRACT\_MAX\_PARALLEL\_DEGREE Option for Data Lake Relational Engine

Sets the maximum parallel degree for the data extraction facility. The TEMP\_EXTRACT\_MAX\_PARALLEL\_DEGREE option limits the maximum number of threads that run in parallel to extract data.



<a name="loio00f65e6745b74f7090225e374f2a80c9__section_ajq_xqq_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loio00f65e6745b74f7090225e374f2a80c9__temp_extract_max_parallel_syntax1"/>

## Syntax

```
TEMP_EXTRACT_MAX_PARALLEL_DEGREE = <value>
```



<a name="loio00f65e6745b74f7090225e374f2a80c9__temp_extract_max_parallel_values1"/>

## Allowed Values

Any non-negative integer.



<a name="loio00f65e6745b74f7090225e374f2a80c9__temp_extract_max_parallel_default1"/>

## Default

64



<a name="loio00f65e6745b74f7090225e374f2a80c9__temp_extract_max_parallel_priv1"/>

## Privileges

Privilege Category: PUBLIC



### 

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loio00f65e6745b74f7090225e374f2a80c9__temp_extract_max_parallel_scope1"/>

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



<a name="loio00f65e6745b74f7090225e374f2a80c9__temp_extract_max_parallel_remarks1"/>

## Remarks

To enable parallel extract, set TEMP\_EXTRACT\_FILE\_PREFIX but not TEMP\_EXTRACT\_NAME1.

For example syntax, see *Extract Data Lake Relational Engine Table Data to Azure Blob Storage* and *Extract Data Lake Relational Engine Table Data to an Amazon S3 Bucket*.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[TEMP_EXTRACT_MAX_PARALLEL_DEGREE Option for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/8b1135ed7e324674bbfaede1484ce890.html "Sets the maximum parallel degree for the data extraction facility. The TEMP_EXTRACT_MAX_PARALLEL_DEGREE option limits the maximum number of threads that run in parallel to extract data.") :arrow_upper_right:

[TEMP\_EXTRACT\_FILE\_PREFIX Option for Data Lake Relational Engine](temp-extract-file-prefix-option-for-data-lake-relational-engine-09cd773.md "Sets the prefix of file name for the generated output file of the data parallel extraction facility. thread_ID starts from 1. filecount starts from 1 for each thread ID. Thefilecount part increments when the size of the output file reaches the file size limit specified by the TEMP_EXTRACT_SIZE option.")

