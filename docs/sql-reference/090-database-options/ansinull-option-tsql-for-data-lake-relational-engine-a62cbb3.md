<!-- loioa62cbb3084f2101595e0e21c42e05c18 -->

# ANSINULL Option \[TSQL\] for Data Lake Relational Engine

Controls the interpretation of using = and != with NULL.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa62cbb3084f2101595e0e21c42e05c18__section_u1n_l5b_qkb"/>

## Syntax

```
ANSINULL = { ON | OFF }
```



<a name="loioa62cbb3084f2101595e0e21c42e05c18__iq_refso_336"/>

## Allowed Values

ON, OFF



<a name="loioa62cbb3084f2101595e0e21c42e05c18__iq_refso_337"/>

## Default

-   ON

-   OFF for Open Client and JDBC connections




<a name="loioa62cbb3084f2101595e0e21c42e05c18__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa62cbb3084f2101595e0e21c42e05c18__iq_refso_325"/>

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



<a name="loioa62cbb3084f2101595e0e21c42e05c18__iq_refso_338"/>

## Remarks

With ANSINULL ON, results of comparisons with NULL using '=' or '!=' are unknown. This includes results of comparisons implied by other operations such as CASE.

Setting ANSINULL ON to OFF allows comparisons with NULL to yield results that are not unknown, for compatibility with SAP Adaptive Server Enterprise.

> ### Note:  
> Unlike SAP SQL Anywhere, data lake Relational Engine does not generate the warning “***null value eliminated in aggregate function***” \(SQLSTATE=01003\) for aggregate functions on columns containing NULL values.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

