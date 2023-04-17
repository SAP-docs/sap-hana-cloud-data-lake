<!-- loioa635b3b984f21015a616cf8663a164c7 -->

# EXTENDED\_JOIN\_SYNTAX Option for Data Lake Relational Engine

Controls whether queries with an ambiguous syntax for multi-table joins are allowed or are reported as an error.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa635b3b984f21015a616cf8663a164c7__section_vpf_xzh_3rb"/>

## Syntax

```
EXTENDED_JOIN_SYNTAX = { ON | OFF }
```



<a name="loioa635b3b984f21015a616cf8663a164c7__iq_refso_524"/>

## Allowed Values

ON, OFF



<a name="loioa635b3b984f21015a616cf8663a164c7__iq_refso_525"/>

## Default

ON



<a name="loioa635b3b984f21015a616cf8663a164c7__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa635b3b984f21015a616cf8663a164c7__iq_refso_325"/>

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



<a name="loioa635b3b984f21015a616cf8663a164c7__iq_refso_526"/>

## Remarks

This option reports a syntax error for those queries containing outer joins that have ambiguous syntax due to the presence of duplicate correlation names on a null-supplying table.

This join clause illustrates the kind of query that is reported where C1 is a condition:

```
( R left outer join T , T  join S on ( C1 ) )
```

If EXTENDED\_JOIN\_SYNTAX is set to ON, this query is interpreted as follows, where C1 and C2 are conditions:

```
( R left outer join T on ( C1 ) ) join S on ( C2 )
```

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

