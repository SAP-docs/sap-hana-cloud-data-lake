<!-- loio1126138de454476ebec9e52012d4511a -->

# TEMP\_EXTRACT\_LENGTH\_PREFIX Option for Data Lake Relational Engine

Adds a prefix field of specified length \(byte\) for a varchar or varbinary column in the generated output file. This PREFIX field in the extract file holds the length of the column data.



<a name="loio1126138de454476ebec9e52012d4511a__section_ajq_xqq_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loio1126138de454476ebec9e52012d4511a__temp_extract_length_prefix_syntax1"/>

## Syntax

```
TEMP_EXTRACT_LENGTH_PREFIX = <value>
```



<a name="loio1126138de454476ebec9e52012d4511a__temp_extract_length_prefix_values1"/>

## Allowed Values

0, 1, 2, 4



<a name="loio1126138de454476ebec9e52012d4511a__temp_extract_length_prefix_default1"/>

## Default

0 \(zero\)



<a name="loio1126138de454476ebec9e52012d4511a__temp_extract_length_prefix_priv1"/>

## Privileges

Privilege Category: PUBLIC



### 

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loio1126138de454476ebec9e52012d4511a__temp_extract_length_prefix_scope1"/>

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



<a name="loio1126138de454476ebec9e52012d4511a__temp_extract_length_prefix_remarks1"/>

## Remarks

If you do not specify TEMP\_EXTRACT\_LENGTH\_PREFIX, or you specify 0 \(the default\), the data extraction facility does not generate a prefix length field.

When you specify any other valid value for TEMP\_EXTRACT\_LENGTH\_PREFIX, the data extraction facility uses that specified value for the length \(byte\) of the prefix field that holds the actual data length, adding it before the actual data for a varchar or varbinary column, including the length for trailing spaces and zeros in the column. If the TEMP\_EXTRACT\_VARYING option is not set, however, the total length of the actual column data in the extracted file is its declared length in a fixed-length format. For example, the data extraction facility always generates 10 bytes for a varchar\(10\) column, necessary to make the file format fixed length.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[TEMP_EXTRACT_LENGTH_PREFIX Option for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/7b609716b74d46c588d7f5a8c64738e7.html "Adds a prefix field of specified length (byte) for a varchar or varbinary column in the generated output file. This PREFIX field in the extract file holds the length of the column data.") :arrow_upper_right:

[TEMP\_EXTRACT\_VARYING Option for Data Lake Relational Engine](temp-extract-varying-option-for-data-lake-relational-engine-ceb244e.md "Used in conjunction with TEMP_EXTRACT_LENGTH_PREFIX, the TEMP_EXTRACT_VARYING option outputs varchar or varbinary column data in a variable-length format in the extracted file. The prefix field specified by TEMP_EXTRACT_LENGTH_PREFIX option holds the length of column data.")

[LOAD TABLE Statement \(Non-Parquet Formats\) for Data Lake Relational Engine](../080-sql-statements/load-table-statement-non-parquet-formats-for-data-lake-relational-engine-7ca3f60.md "Imports data into a data lake Relational Engine database table from either the external object store (Azure BLOB storage, an Amazon S3 bucket, an S3-compliant bucket, or Google Cloud Storage) or from data lake Files containers (the managed object store).")

