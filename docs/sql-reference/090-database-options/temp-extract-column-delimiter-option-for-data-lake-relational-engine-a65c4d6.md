<!-- loioa65c4d6d84f21015907dd85b8bdb1a97 -->

# TEMP\_EXTRACT\_COLUMN\_DELIMITER Option for Data Lake Relational Engine

Specifies the delimiter between columns in the output of the data extraction facility for an ASCII extraction.



<a name="loioa65c4d6d84f21015907dd85b8bdb1a97__section_d3p_24q_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa65c4d6d84f21015907dd85b8bdb1a97__section_zx3_g24_hrb"/>

## Syntax

```
TEMP_EXTRACT_COLUMN_DELIMITER = <string>;
```



<a name="loioa65c4d6d84f21015907dd85b8bdb1a97__iq_refso_992"/>

## Allowed Values

String



<a name="loioa65c4d6d84f21015907dd85b8bdb1a97__iq_refso_993"/>

## Default

','



<a name="loioa65c4d6d84f21015907dd85b8bdb1a97__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa65c4d6d84f21015907dd85b8bdb1a97__iq_refso_994"/>

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



<a name="loioa65c4d6d84f21015907dd85b8bdb1a97__iq_refso_995"/>

## Remarks

Use TEMP\_EXTRACT\_COLUMN\_DELIMITER to specify the delimiter between columns in the output of the data extraction facility. In the case of an ASCII extraction, the default is to separate column values with commas. Strings are unquoted by default.

The delimiter must occupy 1 – 4 bytes, and must be valid in the collation order you are using, if you are using a multibyte collation order. Choose a delimiter that does not occur in any of the data output strings themselves.

If you set this option to the empty string '' for ASCII extractions, the extracted data is written in fixed-width ASCII with no column delimiter. Numeric and binary data types are right-justified on a field of *<n\>* blanks, where *<n\>* is the maximum number of bytes needed for any value of that type. Character data types are left-justified on a field of *<n\>* blanks.

> ### Note:  
> The minimum column width in a fixed-width ASCII extraction is 4 bytes to allow the string “NULL” for a NULL value. For example, if the extracted column is CHAR\(2\) and TEMP\_EXTRACT\_COLUMN\_DELIMITER is set to the empty string '', there are two spaces after the extracted data.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[TEMP\_EXTRACT\_QUOTE Option for Data Lake Relational Engine](temp-extract-quote-option-for-data-lake-relational-engine-a65f5a3.md "Specifies the string to be used as the quote to enclose fields in the output of the data extraction facility for an ASCII extraction, when either the TEMP_EXTRACT_QUOTES option or the TEMP_EXTRACT_QUOTES_ALL option is set ON.")

[TEMP\_EXTRACT\_QUOTES Option for Data Lake Relational Engine](temp-extract-quotes-option-for-data-lake-relational-engine-a65fdb5.md "Specifies that string fields are enclosed in quotes in the output of the data extraction facility for an ASCII extraction.")

[TEMP\_EXTRACT\_QUOTES\_ALL Option for Data Lake Relational Engine](temp-extract-quotes-all-option-for-data-lake-relational-engine-a6605bd.md "Specifies that all fields are enclosed in quotes in the output of the data extraction facility for an ASCII extraction.")

[TEMP\_EXTRACT\_ROW\_DELIMITER Option for Data Lake Relational Engine](temp-extract-row-delimiter-option-for-data-lake-relational-engine-a660d8f.md "Specifies the delimiter between rows in the output of the data extraction facility for an ASCII extraction.")

