<!-- loioa62d7c2684f21015b7059b9e46ca0c56 -->

# ASE\_BINARY\_DISPLAY Option for Data Lake Relational Engine

Specifies that the display of data lake Relational Engine binary columns is consistent with the display of SAP Adaptive Server Enterprise binary columns.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa62d7c2684f21015b7059b9e46ca0c56__section_u1n_l5b_qkb"/>

## Syntax

```
ASE_BINARY_DISPLAY = { ON | OFF }
```



<a name="loioa62d7c2684f21015b7059b9e46ca0c56__iq_refso_354"/>

## Allowed Values

ON, OFF



<a name="loioa62d7c2684f21015b7059b9e46ca0c56__iq_refso_355"/>

## Default

OFF



<a name="loioa62d7c2684f21015b7059b9e46ca0c56__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa62d7c2684f21015b7059b9e46ca0c56__iq_refso_356"/>

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



<a name="loioa62d7c2684f21015b7059b9e46ca0c56__iq_refso_357"/>

## Remarks

ASE\_BINARY\_DISPLAY affects the output of the SELECT statement.

This option pertains to columns in the IQ store. It does not affect variables, catalog store columns or SAP SQL Anywhere columns. When this option is ON, data lake Relational Engine will convert binary data to an ASCII string in hexadecimal format and send that to the client instead. When this option is OFF, data lake Relational Engine will send the binary data as binary.

Set ASE\_BINARY\_DISPLAY OFF to support bulk copy operations on binary data types. Data lake Relational Engine supports bulk loading of remote data via the LOAD TABLE USING CLIENT FILE statement.

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[LOAD TABLE Statement for Data Lake Relational Engine](../080-sql-statements/load-table-statement-for-data-lake-relational-engine-7ca3f60.md "Imports data into a data lake Relational Engine database table from either the external object store (Azure BLOB storage, an Amazon S3 bucket, S3-compliant bucket, or a Google Cloud Storage) or from data lake Files containers (the managed object store).")

[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

