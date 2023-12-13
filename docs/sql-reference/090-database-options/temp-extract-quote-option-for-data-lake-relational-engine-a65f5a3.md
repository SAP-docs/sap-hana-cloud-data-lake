<!-- loioa65f5a3e84f21015ac3ac1ab0990caf8 -->

# TEMP\_EXTRACT\_QUOTE Option for Data Lake Relational Engine

Specifies the string to be used as the quote to enclose fields in the output of the data extraction facility for an ASCII extraction, when either the TEMP\_EXTRACT\_QUOTES option or the TEMP\_EXTRACT\_QUOTES\_ALL option is set ON.



<a name="loioa65f5a3e84f21015ac3ac1ab0990caf8__section_d3p_24q_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa65f5a3e84f21015ac3ac1ab0990caf8__section_zx3_g24_hrb"/>

## Syntax

```
EMP_EXTRACT_QUOTE = <string>;
```



<a name="loioa65f5a3e84f21015ac3ac1ab0990caf8__iq_refso_1018"/>

## Allowed Values

String



<a name="loioa65f5a3e84f21015ac3ac1ab0990caf8__iq_refso_1019"/>

## Default

' ' \(the empty string\)



<a name="loioa65f5a3e84f21015ac3ac1ab0990caf8__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa65f5a3e84f21015ac3ac1ab0990caf8__iq_refso_1020"/>

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



<a name="loioa65f5a3e84f21015ac3ac1ab0990caf8__iq_refso_1021"/>

## Remarks

This option specifies the string to be used as the quote to enclose fields in the output of the data extraction facility for an ASCII extraction, if the default value is not suitable. TEMP\_EXTRACT\_QUOTE is used with the TEMP\_EXTRACT\_QUOTES and TEMP\_EXTRACT\_QUOTES\_ALL options. The quote string specified in the TEMP\_EXTRACT\_QUOTE option has the same restrictions as the row and column delimiters. The default for this option is the empty string, which data lake Relational Engine converts to the single quote mark.

The string specified in the TEMP\_EXTRACT\_QUOTE option must occupy from 1 to a maximum of 4 bytes and must be valid in the collation order you are using, if you are using a multibyte collation order. Be sure to choose a string that does not occur in any of the data output strings themselves.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[TEMP\_EXTRACT\_COLUMN\_DELIMITER Option for Data Lake Relational Engine](temp-extract-column-delimiter-option-for-data-lake-relational-engine-a65c4d6.md "Specifies the delimiter between columns in the output of the data extraction facility for an ASCII extraction.")

[TEMP\_EXTRACT\_QUOTES Option for Data Lake Relational Engine](temp-extract-quotes-option-for-data-lake-relational-engine-a65fdb5.md "Specifies that string fields are enclosed in quotes in the output of the data extraction facility for an ASCII extraction.")

[TEMP\_EXTRACT\_QUOTES\_ALL Option for Data Lake Relational Engine](temp-extract-quotes-all-option-for-data-lake-relational-engine-a6605bd.md "Specifies that all fields are enclosed in quotes in the output of the data extraction facility for an ASCII extraction.")

