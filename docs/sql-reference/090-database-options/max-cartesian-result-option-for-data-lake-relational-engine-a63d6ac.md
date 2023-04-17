<!-- loioa63d6acb84f21015b360dbd872a144c9 -->

# MAX\_CARTESIAN\_RESULT Option for Data Lake Relational Engine 

Limits the number of rows resulting from a Cartesian join.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa63d6acb84f21015b360dbd872a144c9__section_zx3_g24_hrb"/>

## Syntax

```
MAX_CARTESIAN_RESULT = <integer>
```



<a name="loioa63d6acb84f21015b360dbd872a144c9__iq_refso_710"/>

## Allowed Values

Integer



<a name="loioa63d6acb84f21015b360dbd872a144c9__iq_refso_711"/>

## Default

100,000,000



<a name="loioa63d6acb84f21015b360dbd872a144c9__section_fgs_dy3_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa63d6acb84f21015b360dbd872a144c9__iq_refso_712"/>

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



<a name="loioa63d6acb84f21015b360dbd872a144c9__iq_refso_713"/>

## Remarks

MAX\_CARTESIAN\_RESULT limits the number of result rows from a query containing a Cartesian join \(usually the result of missing one or more join conditions when creating the query\). If data lake Relational EngineMAX\_CARTESIAN\_RESULT to 0 disables the check for the number of result rows of a Cartesian join. cannot find a query plan for the Cartesian join with an estimated result under this limit, it rejects the query and returns an error. Setting

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

