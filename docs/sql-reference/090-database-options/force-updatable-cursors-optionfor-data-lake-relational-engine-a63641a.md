<!-- loioa63641a184f210159a17a6f150ad716c -->

# FORCE\_UPDATABLE\_CURSORS Optionfor Data Lake Relational Engine

Controls whether cursors that have not been declared as updatable can be updated.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa63641a184f210159a17a6f150ad716c__section_tfh_pzh_3rb"/>

## Syntax

```
FORCE_UPDATABLE_CURSOR = { ON | OFF }
```



<a name="loioa63641a184f210159a17a6f150ad716c__iq_refso_536"/>

## Allowed Values

ON, OFF



<a name="loioa63641a184f210159a17a6f150ad716c__iq_refso_537"/>

## Default

OFF



<a name="loioa63641a184f210159a17a6f150ad716c__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa63641a184f210159a17a6f150ad716c__iq_refso_538"/>

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



<a name="loioa63641a184f210159a17a6f150ad716c__iq_refso_539"/>

## Remarks

When FORCE\_UPDATABLE\_CURSORS is ON, cursors that have not been declared as updatable can be updated. This option allows updatable cursors to be used in front-end applications without specifying the FOR UPDATE clause of the DECLARE CURSOR statement.

> ### Caution:  
> Do not use FORCE\_UPDATABLE\_CURSORS unless absolutely necessary.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

