<!-- loioa62c5c2784f21015ae45e582babaa461 -->

# ANSI\_CLOSE\_CURSORS\_ON\_ROLLBACK Option \[TSQL\] for Data Lake Relational Engine

Controls whether cursors that were opened WITH HOLD are closed when a ROLLBACK is performed.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa62c5c2784f21015ae45e582babaa461__section_u1n_l5b_qkb"/>

## Syntax

```
ANSI_CLOSE_CURSORS_ON_ROLLBACK = ON
```



<a name="loioa62c5c2784f21015ae45e582babaa461__iq_refso_330"/>

## Allowed Values

ON



<a name="loioa62c5c2784f21015ae45e582babaa461__iq_refso_331"/>

## Default

ON



<a name="loioa62c5c2784f21015ae45e582babaa461__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa62c5c2784f21015ae45e582babaa461__iq_refso_325"/>

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



<a name="loioa62c5c2784f21015ae45e582babaa461__iq_refso_332"/>

## Remarks

The ANSI SQL/3 standard requires all cursors be closed when a transaction is rolled back. This option forces that behavior and can't be changed. The CLOSE\_ON\_ENDTRANS option overrides this option.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[CLOSE\_ON\_ENDTRANS Option \[TSQL\] for Data Lake Relational Engine](close-on-endtrans-option-tsql-for-data-lake-relational-engine-a62fbb7.md "Controls closing of cursors at the end of a transaction.")

