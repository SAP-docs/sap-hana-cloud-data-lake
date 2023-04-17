<!-- loioa65e506784f21015b207e8280c3fc6b0 -->

# TEMP\_EXTRACT\_NULL\_AS\_EMPTY Option for Data Lake Relational Engine

Controls the representation of null values in the output of the data extraction facility for an ASCII extraction.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa65e506784f21015b207e8280c3fc6b0__section_sxb_tph_mrb"/>

## Syntax

```
TEMP_EXTRACT_NULL_AS_EMPTY = { ON | OFF }
```



<a name="loioa65e506784f21015b207e8280c3fc6b0__iq_refso_1010"/>

## Allowed Values

ON, OFF



<a name="loioa65e506784f21015b207e8280c3fc6b0__iq_refso_1011"/>

## Default

OFF



<a name="loioa65e506784f21015b207e8280c3fc6b0__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa65e506784f21015b207e8280c3fc6b0__iq_refso_1012"/>

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



<a name="loioa65e506784f21015b207e8280c3fc6b0__iq_refso_1013"/>

## Remarks

TEMP\_EXTRACT\_NULL\_AS\_EMPTY controls the representation of null values in the output of the data extraction facility for ASCII extractions. When the TEMP\_EXTRACT\_NULL\_AS\_EMPTY option is set to ON, a null value is represented as '' \(the empty string\) for all data types.

The quotes shown above are not present in the extract output file. When the TEMP\_EXTRACT\_NULL\_AS\_EMPTY option is set to OFF, the string 'NULL' is used in all cases to represent a NULL value. OFF is the default value.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

