<!-- loio09cd773ef6924c119dd3adea2e91bd96 -->

# TEMP\_EXTRACT\_FILE\_PREFIX Option for Data Lake Relational Engine

Sets the prefix of file name for the generated output file of the data parallel extraction facility. *<thread\_ID\>* starts from 1. *<filecount\>* starts from 1 for each thread ID. The*<filecount\>* part increments when the size of the output file reaches the file size limit specified by the TEMP\_EXTRACT\_SIZE option.



<a name="loio09cd773ef6924c119dd3adea2e91bd96__section_ajq_xqq_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loio09cd773ef6924c119dd3adea2e91bd96__temp_extract_file_prefix_syntax1"/>

## Syntax

```
TEMP_EXTRACT_FILE_PREFIX = <string>;
```



<a name="loio09cd773ef6924c119dd3adea2e91bd96__temp_extract_file_prefix_values1"/>

## Allowed Values

String containing a prefix of the output filename.



<a name="loio09cd773ef6924c119dd3adea2e91bd96__temp_extract_file_prefix_default1"/>

## Default

*<prefix\>**<thread\_ID\>*\_*<filecount\>*



<a name="loio09cd773ef6924c119dd3adea2e91bd96__temp_extract_file_prefix_priv1"/>

## Privileges

Privilege Category: PUBLIC



### 

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loio09cd773ef6924c119dd3adea2e91bd96__temp_extract_file_prefix_scope1"/>

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



<a name="loio09cd773ef6924c119dd3adea2e91bd96__temp_extract_file_prefix_remarks1"/>

## Remarks

Use parallel extraction to extract to data lake Files storage, Azure storage, or AWS storage.

The TEMP\_EXTRACT\_APPEND option is not compatible with the parallel extraction facility. If the output files do not already exist, parallel extraction facility creates the new files. If the output files already exist, the file contents are overwritten.

Use the parallel data extraction facility when the data set to extract is large and you need better performance. When the parallel extract is enabled, multiple output files could be generated depending on the number of threads used to extract in parallel.

If the TEMP\_EXTRACT\_DIRECTORY option is set to a valid directory path, parallel temp extract files are placed in that directory. If TEMP\_EXTRACT\_DIRECTORY option is blank, then parallel temp extract files are by default placed in the server startup directory.

To enable parallel extract, set TEMP\_EXTRACT\_FILE\_PREFIX but not TEMP\_EXTRACT\_NAME1.



## Example

For example, the parameters below generate files `extract_file1_1.csv`, `extract_file2_1.csv`, `extract_file3_1.csv`, and `extract_file4_1.csv`, and set the parallel degree 4.

```
SET OPTION PUBLIC.Temp_Extract_File_Prefix = "extract_file";
;
```

```
SET OPTION PUBLIC.Temp_Extract_File_Extension = "csv";
;
```

```
SET OPTION PUBLIC.Temp_Extract_Max_Parallel_Degree = 4;

```

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[TEMP_EXTRACT_FILE_PREFIX Option for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/af977f36d280410dba64b6bfe2608179.html "Sets the prefix of file name for the generated output file of the data parallel extraction facility. thread_ID starts from 1. filecount starts from 1 for each thread ID. Thefilecount part increments when the size of the output file reaches the file size limit specified by the TEMP_EXTRACT_SIZE option.") :arrow_upper_right:

[TEMP\_EXTRACT\_FILE\_EXTENSION Option for Data Lake Relational Engine](temp-extract-file-extension-option-for-data-lake-relational-engine-896be73.md "Sets the file name extension for the generated output file of the data parallel extraction facility. When you specify the TEMP_EXTRACT_FILE_EXTENSION option, each file name generated becomes prefix thread_ID_filecount.file extension.")

[TEMP\_EXTRACT\_MAX\_PARALLEL\_DEGREE Option for Data Lake Relational Engine](temp-extract-max-parallel-degree-option-for-data-lake-relational-engine-00f65e6.md "Sets the maximum parallel degree for the data extraction facility. The TEMP_EXTRACT_MAX_PARALLEL_DEGREE option limits the maximum number of threads that run in parallel to extract data.")

[TEMP\_EXTRACT\_SIZE Option for Data Lake Relational Engine](temp-extract-size-option-for-data-lake-relational-engine-096c15c.md "Sets the maximum size (KB) of the corresponding output files generated by the parallel data extraction facility.")

