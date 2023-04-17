<!-- loioa6605bde84f210158ad1be3b32e12f3d -->

# TEMP\_EXTRACT\_QUOTES\_ALL Option for Data Lake Relational Engine

Specifies that all fields are enclosed in quotes in the output of the data extraction facility for an ASCII extraction.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa6605bde84f210158ad1be3b32e12f3d__section_g1g_bqh_mrb"/>

## Syntax

```
TEMP_EXTRACT_QUOTES_ALL = { ON | OFF }
```



<a name="loioa6605bde84f210158ad1be3b32e12f3d__iq_refso_1026"/>

## Allowed Values

ON, OFF



<a name="loioa6605bde84f210158ad1be3b32e12f3d__iq_refso_1027"/>

## Default

OFF



<a name="loioa6605bde84f210158ad1be3b32e12f3d__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa6605bde84f210158ad1be3b32e12f3d__iq_refso_1028"/>

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



<a name="loioa6605bde84f210158ad1be3b32e12f3d__iq_refso_1029"/>

## Remarks

TEMP\_EXTRACT\_QUOTES\_ALL specifies that all fields are enclosed in quotes in the output of the data extraction facility for an ASCII extraction. The string used as the quote is specified in TEMP\_EXTRACT\_QUOTE, if the default is not suitable.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[TEMP\_EXTRACT\_COLUMN\_DELIMITER Option for Data Lake Relational Engine](temp-extract-column-delimiter-option-for-data-lake-relational-engine-a65c4d6.md "Specifies the delimiter between columns in the output of the data extraction facility for an ASCII extraction.")

[TEMP\_EXTRACT\_QUOTES Option for Data Lake Relational Engine](temp-extract-quotes-option-for-data-lake-relational-engine-a65fdb5.md "Specifies that string fields are enclosed in quotes in the output of the data extraction facility for an ASCII extraction.")

[TEMP\_EXTRACT\_QUOTES\_ALL Option for Data Lake Relational Engine](temp-extract-quotes-all-option-for-data-lake-relational-engine-a6605bd.md "Specifies that all fields are enclosed in quotes in the output of the data extraction facility for an ASCII extraction.")

[TEMP\_EXTRACT\_ROW\_DELIMITER Option for Data Lake Relational Engine](temp-extract-row-delimiter-option-for-data-lake-relational-engine-a660d8f.md "Specifies the delimiter between rows in the output of the data extraction facility for an ASCII extraction.")

