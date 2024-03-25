<!-- loioaef24bc01a494d68b62e2b6dfeabff56 -->

# TEMP\_EXTRACT\_COMPRESS Option for Data Lake Relational Engine

Writes the output file for exports in gzip format. This results in a significant savings of storagespace when exporting tables.



<a name="loioaef24bc01a494d68b62e2b6dfeabff56__section_fq2_gpq_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioaef24bc01a494d68b62e2b6dfeabff56__temp_extract_compress_syntax1"/>

## Syntax

```
TEMP_EXTRACT_COMPRESS = { ON | OFF }
```



<a name="loioaef24bc01a494d68b62e2b6dfeabff56__temp_extract_compress_values1"/>

## Allowed Values

ON, OFF



<a name="loioaef24bc01a494d68b62e2b6dfeabff56__temp_extract_compress_default1"/>

## Default

OFF



<a name="loioaef24bc01a494d68b62e2b6dfeabff56__temp_extract_compress_priv1"/>

## Privileges

Privilege Category: PUBLIC



### 

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioaef24bc01a494d68b62e2b6dfeabff56__temp_extract_compress_scope1"/>

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



<a name="loioaef24bc01a494d68b62e2b6dfeabff56__temp_extract_compress_remarks1"/>

## Remarks

This option cannot be used with the TEMP\_EXTRACT\_APPEND, TEMP\_EXTRACT\_SIZE, or TEMP\_EXTRACT\_SIZE*<n\>* options.

In parallel mode, the TEMP\_EXTRACT\_FILE\_EXTENSION option must be set to gz or '' \(empty string\). In serial mode, the TEMP\_EXTRACT\_NAME*<n\>* option must end with .gz.

**Related Information**  


[TEMP\_EXTRACT\_FILE\_EXTENSION Option for Data Lake Relational Engine](temp-extract-file-extension-option-for-data-lake-relational-engine-896be73.md "Sets the file name extension for the generated output file of the data parallel extraction facility. When you specify the TEMP_EXTRACT_FILE_EXTENSION option, each file name generated becomes prefix thread_ID_filecount.file extension.")

[TEMP_EXTRACT_COMPRESS Option for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/aa37821e445f4177b189aad7442f104d.html "Writes the output file for exports in gzip format. This results in a significant savings of storagespace when exporting tables.") :arrow_upper_right:

