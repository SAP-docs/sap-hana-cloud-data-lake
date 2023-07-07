<!-- loioa63914eb84f21015b454db5374017eb5 -->

# IDENTITY\_INSERT Option for Data Lake Relational Engine

Enables users to insert values into or to update an IDENTITY or AUTOINCREMENT column.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa63914eb84f21015b454db5374017eb5__identity_insert_syntax1"/>

## Syntax

```
IDENTITY_INSERT = <datalake_table_name>
```



<a name="loioa63914eb84f21015b454db5374017eb5__identity_insert_values1"/>

## Allowed Values

= '*<tablename\>*'



<a name="loioa63914eb84f21015b454db5374017eb5__identity_insert_default1"/>

## Default

Option not set.



<a name="loioa63914eb84f21015b454db5374017eb5__identity_priv1"/>

## Privileges

Privilege Category: PUBLIC



### 

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa63914eb84f21015b454db5374017eb5__identity_insert_scope1"/>

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

> ### Note:  
> If you set a user level option for the current option, the corresponding temporary option is also set. See *Scope and Duration of Database Options*.



<a name="loioa63914eb84f21015b454db5374017eb5__identity_insert_remarks1"/>

## Remarks

When IDENTITY\_INSERT is set, insert/update is enabled. A table name must be specified to identify the column to insert or update. If you are not the table owner, qualify the table name with the owner name.

To drop a table with an IDENTITY column, IDENTITY\_INSERT must not be set to that table.



<a name="loioa63914eb84f21015b454db5374017eb5__identity_insert_examples1"/>

## Examples

If you use the table Employees to run explicit inserts:

```
SET TEMPORARY OPTION IDENTITY_INSERT = 'HDLADMIN.Employees'
```

To turn the option off, specify the equals sign and an empty string:

```
SET TEMPORARY OPTION IDENTITY_INSERT = ''
```

Illustrates the effect of user level options on temporary options \(see *Note*\), if you are connected to the database as HDLADMIN and enter:

```
SET OPTION IDENTITY_INSERT = 'Customers'
```

The value for the option is set to Customers for the user HDLADMIN and temporary for the current connection. Other users who subsequently connect to the database as HDLADMIN find their option value for IDENTITY\_INSERT is Customers also.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[IDENTITY_INSERT Option for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/3122a9a6dcee455791a4097b41c21407.html "Enables users to insert values into or to update an IDENTITY or AUTOINCREMENT column.") :arrow_upper_right:

[Scope and Duration of Database Options](scope-and-duration-of-database-options-a629c37.md "You can set options at three levels of scope: public, user, and temporary.")

[QUERY\_PLAN Option for Data Lake Relational Engine](query-plan-option-for-data-lake-relational-engine-a64d3bd.md "Specifies whether or not additional query plans are printed to the data lake Relational Engine message file.")

