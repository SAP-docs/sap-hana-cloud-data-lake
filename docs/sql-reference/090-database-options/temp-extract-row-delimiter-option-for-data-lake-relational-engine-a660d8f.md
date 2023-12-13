<!-- loioa660d8f184f21015b72af7659f669254 -->

# TEMP\_EXTRACT\_ROW\_DELIMITER Option for Data Lake Relational Engine

Specifies the delimiter between rows in the output of the data extraction facility for an ASCII extraction.



<a name="loioa660d8f184f21015b72af7659f669254__section_cc4_xsr_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa660d8f184f21015b72af7659f669254__section_zx3_g24_hrb"/>

## Syntax

```
TEMP_EXTRACT_ROW_DELIMITER = <string>;
```



<a name="loioa660d8f184f21015b72af7659f669254__iq_refso_1030"/>

## Allowed Values

String



<a name="loioa660d8f184f21015b72af7659f669254__iq_refso_1031"/>

## Default

See *Remarks* section.



<a name="loioa660d8f184f21015b72af7659f669254__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa660d8f184f21015b72af7659f669254__iq_refso_1032"/>

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



<a name="loioa660d8f184f21015b72af7659f669254__iq_refso_1033"/>

## Remarks

TEMP\_EXTRACT\_ROW\_DELIMITER specifies the delimiter between rows in the output of the data extraction facility.

For ASCII extractions, the default is to end the row with a newline character \(LF\).

-   If you don't set a value, then data lake Relational Engine uses LF for the delimiter.

-   If you set TEMP\_EXTRACT\_ROW\_DELIMITER to the empty string \(''\), then data lake Relational Engine uses LF for the delimiter.

-   If you set TEMP\_EXTRACT\_ROW\_DELIMITER to any other value \(fewer than 4 characters\), then data lake Relational Engine uses that value for the delimiter.


The delimiter must occupy 1–4 bytes and must be valid in the collation order you're using, if you’re using a multibyte collation order. Choose a delimiter that doesn't occur in any of the data output strings.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[TEMP\_EXTRACT\_COLUMN\_DELIMITER Option for Data Lake Relational Engine](temp-extract-column-delimiter-option-for-data-lake-relational-engine-a65c4d6.md "Specifies the delimiter between columns in the output of the data extraction facility for an ASCII extraction.")

[TEMP\_EXTRACT\_QUOTES Option for Data Lake Relational Engine](temp-extract-quotes-option-for-data-lake-relational-engine-a65fdb5.md "Specifies that string fields are enclosed in quotes in the output of the data extraction facility for an ASCII extraction.")

[TEMP\_EXTRACT\_QUOTES\_ALL Option for Data Lake Relational Engine](temp-extract-quotes-all-option-for-data-lake-relational-engine-a6605bd.md "Specifies that all fields are enclosed in quotes in the output of the data extraction facility for an ASCII extraction.")

