<!-- loioa65ed25d84f21015ba47da948bcf0bfb -->

# TEMP\_EXTRACT\_NULL\_AS\_ZERO Option for Data Lake Relational Engine

Controls the representation of null values in the output of the data extraction facility for an ASCII extraction.



<a name="loioa65ed25d84f21015ba47da948bcf0bfb__section_jb5_qsr_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa65ed25d84f21015ba47da948bcf0bfb__section_pbh_qqh_mrb"/>

## Syntax

```
TEMP_EXTRACT_NULL_AS_ZERO = { ON | OFF };
```



<a name="loioa65ed25d84f21015ba47da948bcf0bfb__iq_refso_1014"/>

## Allowed Values

ON, OFF



<a name="loioa65ed25d84f21015ba47da948bcf0bfb__iq_refso_1015"/>

## Default

OFF



<a name="loioa65ed25d84f21015ba47da948bcf0bfb__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa65ed25d84f21015ba47da948bcf0bfb__iq_refso_1016"/>

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



<a name="loioa65ed25d84f21015ba47da948bcf0bfb__iq_refso_1017"/>

## Remarks

TEMP\_EXTRACT\_NULL\_AS\_ZERO controls the representation of null values in the output of the data extraction facility for ASCII extractions. When TEMP\_EXTRACT\_NULL\_AS\_ZERO is set to ON, a null value is represented as follows:

-   '0' – arithmetic type
-   ' ' \(the empty string\) – the CHAR and VARCHAR character types
-   ' ' \(the empty string\) – dates
-   ' ' \(the empty string\) – times
-   ' ' \(the empty string\) – timestamps

The quotes shown above are not present in the extract output file. When the TEMP\_EXTRACT\_NULL\_AS\_ZERO option is set to OFF, the string 'NULL' is used in all cases to represent a NULL value. OFF is the default value.

> ### Note:  
> An ASCII extract from a CHAR or VARCHAR column in a table always returns at least four characters to the output file. This is required if TEMP\_EXTRACT\_NULL\_AS\_ZERO is set to OFF, because data lake Relational Engine needs to write out the word NULL for any row in a column that has a null value. Reserving four spaces is not required if TEMP\_EXTRACT\_NULL\_AS\_ZERO is set to ON.
> 
> If TEMP\_EXTRACT\_NULL\_AS\_ZERO is set to ON, the number of characters that an ASCII extract writes to a file for a CHAR or VARCHAR column equals the number of characters in the column, even if that number is less than four.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

