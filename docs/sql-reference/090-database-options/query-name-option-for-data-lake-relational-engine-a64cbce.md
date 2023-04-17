<!-- loioa64cbcec84f21015a49bf2d389632729 -->

# QUERY\_NAME Option for Data Lake Relational Engine

Gives a name to an executed query in its query plan.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa64cbcec84f21015a49bf2d389632729__query_name_syntax1"/>

## Syntax

```
QUERY_NAME = <string_expression>
```



<a name="loioa64cbcec84f21015a49bf2d389632729__query_name_values1"/>

## Allowed Values

Quote-delimited string of up to 80 characters.



<a name="loioa64cbcec84f21015a49bf2d389632729__query_name_default1"/>

## Default

' ' \(the empty string\)



<a name="loioa64cbcec84f21015a49bf2d389632729__query_name_priv1"/>

## Privileges

Privilege Category: PUBLIC



### 

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa64cbcec84f21015a49bf2d389632729__query_name_scope1"/>

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



<a name="loioa64cbcec84f21015a49bf2d389632729__query_name_remarks1"/>

## Remarks

You can assign the QUERY\_NAME option any quote-delimited string value, up to 80 characters. For example:

```
set temporary option Query_Name = 'my third query'
```

When this option is set, query plans that are sent to the `.iqmsg` file or `.html` file include a line near the top of the plan that looks like:

```
Query_Name:  'my third query'
```

If you set the option to a different value before each query in a script, it is much easier to identify the correct query plan for a particular query. The query name is also added to the file name for HTML query plans. This option has no other effect on the query.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[QUERY_NAME Option for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/46c2fe6f4e30441c982519451fa6a6bf.html "Gives a name to an executed query in its query plan.") :arrow_upper_right:

