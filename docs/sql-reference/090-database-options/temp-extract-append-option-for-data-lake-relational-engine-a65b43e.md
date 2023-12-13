<!-- loioa65b43e184f21015a50fca8217c1fe45 -->

# TEMP\_EXTRACT\_APPEND Option for Data Lake Relational Engine

Specifies that any rows extracted by the data extraction facility are added to the end of an output file.



<a name="loioa65b43e184f21015a50fca8217c1fe45__section_ucg_xsr_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa65b43e184f21015a50fca8217c1fe45__section_qkq_jqh_mrb"/>

## Syntax

```
TEMP_EXTRACT_APPEND = { ON | OFF };
```



<a name="loioa65b43e184f21015a50fca8217c1fe45__iq_refso_983"/>

## Allowed Values

ON, OFF



<a name="loioa65b43e184f21015a50fca8217c1fe45__iq_refso_984"/>

## Default

OFF



<a name="loioa65b43e184f21015a50fca8217c1fe45__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa65b43e184f21015a50fca8217c1fe45__iq_refso_985"/>

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



<a name="loioa65b43e184f21015a50fca8217c1fe45__iq_refso_986"/>

## Remarks

This option specifies that any rows extracted by the data extraction facility are added to the end of an output file. You create the output file in a directory where you have WRITE/EXECUTE permissions and you set WRITE permission on the directory and output file for the user name used to start data lake Relational Engine. You can give permissions on the output file to other users as appropriate. The name of the output file is specified in the TEMP\_EXTRACT\_NAME1 option. The data extraction facility creates the output file, if the file does not already exist.

TEMP\_EXTRACT\_APPEND is not compatible with the TEMP\_EXTRACT\_SIZE*<\>* or TEMP\_EXTRAC\_COMPRESS options. If you try to restrict the size of or compress the extract append output file, data lake Relational Engine reports an error.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[TEMP\_EXTRACT\_NAME<N\> Option for Data Lake Relational Engine](temp-extract-name-n-option-for-data-lake-relational-engine-a65dd19.md "Specifies the data lake Filescontainer object file name, or theAzure block blob name, or the Amazon S3 bucket object name you’re extracting to. You must specify the name when extracting data from data lake Relational Engine to cloud storage.")

