<!-- loioa6452a6184f21015b39cccaeb9e95656 -->

# ODBC\_DISTINGUISH\_CHAR\_AND\_VARCHAR Option for Data Lake Relational Engine

Controls how the data lake Relational Engine ODBC driver describes CHAR columns.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa6452a6184f21015b39cccaeb9e95656__section_ssb_yws_lrb"/>

## Syntax

```
ODBC_DISTINGUISH_CHAR_AND_VARCHAR = { ON | OFF }
```



<a name="loioa6452a6184f21015b39cccaeb9e95656__iq_refso_809"/>

## Allowed Values

ON, OFF



<a name="loioa6452a6184f21015b39cccaeb9e95656__iq_refso_810"/>

## Default

OFF



<a name="loioa6452a6184f21015b39cccaeb9e95656__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa6452a6184f21015b39cccaeb9e95656__iq_refso_325"/>

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



<a name="loioa6452a6184f21015b39cccaeb9e95656__iq_refso_811"/>

## Remarks

When a connection is opened, the data lake Relational Engine ODBC driver uses the setting of this option to determine how CHAR columns are described. If ODBC\_DISTINGUISH\_CHAR\_AND\_VARCHAR is set to OFF \(the default\), then CHAR columns are described as SQL\_VARCHAR. If this option is set to ON, then CHAR columns are described as SQL\_CHAR. VARCHAR columns are always described as SQL\_VARCHAR.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

