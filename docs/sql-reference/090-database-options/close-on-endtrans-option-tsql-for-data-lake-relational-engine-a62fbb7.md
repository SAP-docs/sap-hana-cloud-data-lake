<!-- loioa62fbb7984f210158654ff7e4d0f48d7 -->

# CLOSE\_ON\_ENDTRANS Option \[TSQL\] for Data Lake Relational Engine

Controls closing of cursors at the end of a transaction.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa62fbb7984f210158654ff7e4d0f48d7__section_xdr_2ry_brb"/>

## Syntax

```
CLOSE_ON_ENDTRANS  = ON
```



<a name="loioa62fbb7984f210158654ff7e4d0f48d7__iq_refso_405"/>

## Allowed Values

ON



<a name="loioa62fbb7984f210158654ff7e4d0f48d7__iq_refso_406"/>

## Default

ON



<a name="loioa62fbb7984f210158654ff7e4d0f48d7__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa62fbb7984f210158654ff7e4d0f48d7__iq_refso_325"/>

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



<a name="loioa62fbb7984f210158654ff7e4d0f48d7__iq_refso_407"/>

## Remarks

When CLOSE\_ON\_ENDTRANS is set to ON \(the default and only value allowed\), cursors are closed at the end of a transaction, which is Transact-SQL compatible behavior.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

