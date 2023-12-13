<!-- loio896be73dcdea4e83868592ad56c2d1e4 -->

# TEMP\_EXTRACT\_FILE\_EXTENSION Option for Data Lake Relational Engine

Sets the file name extension for the generated output file of the data parallel extraction facility. When you specify the TEMP\_EXTRACT\_FILE\_EXTENSION option, each file name generated becomes *<prefix\>* *<thread\_ID\>*\_*<filecount\>*.*<file extension\>*.



<a name="loio896be73dcdea4e83868592ad56c2d1e4__section_d3p_24q_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loio896be73dcdea4e83868592ad56c2d1e4__section_zx3_g24_hrb"/>

## Syntax

```
TEMP_EXTRACT_FILE_EXTENSION = <string>;
```



## Allowed Values

String containing a file name extension



<a name="loio896be73dcdea4e83868592ad56c2d1e4__iq_refso_1002"/>

## Default

' ' \(the empty string\)



<a name="loio896be73dcdea4e83868592ad56c2d1e4__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



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



<a name="loio896be73dcdea4e83868592ad56c2d1e4__iq_refso_1004"/>

## Remarks

This filename extension is used in parallel temporary extract operations. To enable parallel extract, set TEMP\_EXTRACT\_FILE\_PREFIX but not TEMP\_EXTRACT\_NAME*<n\>*. If you set TEMP\_EXTRACT\_COMPRESS, the TEMP\_EXTRACT\_FILE\_EXTENSION option must either be set to '' \(the default value\) or to 'gz'. Other file extensions report an error.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[TEMP\_EXTRACT\_FILE\_PREFIX Option for Data Lake Relational Engine](temp-extract-file-prefix-option-for-data-lake-relational-engine-09cd773.md "Sets the prefix of file name for the generated output file of the data parallel extraction facility. thread_ID starts from 1. filecount starts from 1 for each thread ID. Thefilecount part increments when the size of the output file reaches the file size limit specified by the TEMP_EXTRACT_SIZE option.")

[TEMP\_EXTRACT\_COMPRESS Option for Data Lake Relational Engine](temp-extract-compress-option-for-data-lake-relational-engine-aef24bc.md "Writes the output file for exports in gzip format. This results in a significant savings of storagespace when exporting tables.")

