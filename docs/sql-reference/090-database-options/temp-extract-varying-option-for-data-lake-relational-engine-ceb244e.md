<!-- loioceb244e0d1974ae5a432814d38640f9d -->

# TEMP\_EXTRACT\_VARYING Option for Data Lake Relational Engine

Used in conjunction with TEMP\_EXTRACT\_LENGTH\_PREFIX, the TEMP\_EXTRACT\_VARYING option outputs varchar or varbinary column data in a variable-length format in the extracted file. The prefix field specified by TEMP\_EXTRACT\_LENGTH\_PREFIX option holds the length of column data.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioceb244e0d1974ae5a432814d38640f9d__temp_extract_varying_syntax1"/>

## Syntax

```
TEMP_EXTRACT_VARYING = { ON | OFF }
```



<a name="loioceb244e0d1974ae5a432814d38640f9d__temp_extract_varying_values1"/>

## Allowed Values

ON, OFF



<a name="loioceb244e0d1974ae5a432814d38640f9d__temp_extract_varying_default1"/>

## Default

OFF



<a name="loioceb244e0d1974ae5a432814d38640f9d__temp_extract_varying_priv1"/>

## Privileges

Privilege Category: PUBLIC



### 

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioceb244e0d1974ae5a432814d38640f9d__temp_extract_varying_scope1"/>

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



<a name="loioceb244e0d1974ae5a432814d38640f9d__temp_extract_varying_remarks1"/>

## Remarks

You can only use TEMP\_EXTRACT\_VARYING for varchar and varbinary columns in a binary mode extraction.

When you set TEMP\_EXTRACT\_VARYING to ON, the data field in the extracted file becomes variable length \(with a prefix field\). The data field occupies only the data length in the extracted file, instead of the declared length of the varchar or varbinary column, so that there is no trailing padding.

Use this option with TEMP\_EXTRACT\_LENGTH\_PREFIX to indicate the data length in the extracted file; there is no column delimiter in binary mode extractions.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[TEMP_EXTRACT_VARYING Option for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/a975dc54ec404d3a9667cbc0dd8e9e6c.html "Used in conjunction with TEMP_EXTRACT_LENGTH_PREFIX, the TEMP_EXTRACT_VARYING option outputs varchar or varbinary column data in a variable-length format in the extracted file. The prefix field specified by TEMP_EXTRACT_LENGTH_PREFIX option holds the length of column data.") :arrow_upper_right:

[TEMP\_EXTRACT\_LENGTH\_PREFIX Option for Data Lake Relational Engine](temp-extract-length-prefix-option-for-data-lake-relational-engine-1126138.md "Adds a prefix field of specified length (byte) for a varchar or varbinary column in the generated output file. This PREFIX field in the extract file holds the length of the column data.")

