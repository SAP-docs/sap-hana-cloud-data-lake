<!-- loioa65d50c284f21015b6a1e84593ece6ce -->

# TEMP\_EXTRACT\_ESCAPE\_QUOTES Option for Data Lake Relational Engine

Specifies whether all quotes in fields containing quotes are escaped in the output of the data extraction facility for an ASCII extraction.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa65d50c284f21015b6a1e84593ece6ce__section_hkg_lqh_mrb"/>

## Syntax

```
TEMP_EXTRACT_ESCAPE_QUOTES = { ON | OFF }
```



<a name="loioa65d50c284f21015b6a1e84593ece6ce__iq_refso_1001"/>

## Allowed Values

ON, OFF



<a name="loioa65d50c284f21015b6a1e84593ece6ce__iq_refso_1002"/>

## Default

OFF



<a name="loioa65d50c284f21015b6a1e84593ece6ce__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa65d50c284f21015b6a1e84593ece6ce__iq_refso_1003"/>

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



<a name="loioa65d50c284f21015b6a1e84593ece6ce__iq_refso_1004"/>

## Remarks

This option is ignored unless TEMP\_EXTRACT\_QUOTE is the default or set to the value of '"' \(double quotes\), and TEMP\_EXTRACT\_BINARY is OFF, and either TEMP\_EXTRACT\_QUOTES or TEMP\_EXTRACT\_QUOTES\_ALL is ON.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[TEMP\_EXTRACT\_BINARY Option for Data Lake Relational Engine](temp-extract-binary-option-for-data-lake-relational-engine-a65bc23.md "In combination with the TEMP_EXTRACT_SWAP option, specifies the type of extraction performed by the data extraction facility.")

[TEMP\_EXTRACT\_QUOTES Option for Data Lake Relational Engine](temp-extract-quotes-option-for-data-lake-relational-engine-a65fdb5.md "Specifies that string fields are enclosed in quotes in the output of the data extraction facility for an ASCII extraction.")

[TEMP\_EXTRACT\_QUOTES\_ALL Option for Data Lake Relational Engine](temp-extract-quotes-all-option-for-data-lake-relational-engine-a6605bd.md "Specifies that all fields are enclosed in quotes in the output of the data extraction facility for an ASCII extraction.")

