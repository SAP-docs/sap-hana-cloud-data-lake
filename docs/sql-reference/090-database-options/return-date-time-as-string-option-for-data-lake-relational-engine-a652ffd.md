<!-- loioa652ffd684f2101583dcef31685601cf -->

# RETURN\_DATE\_TIME\_AS\_STRING Option for Data Lake Relational Engine

Controls how a date, time, or timestamp value is passed to the client application when queried.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa652ffd684f2101583dcef31685601cf__return_date_time_syntax1"/>

## Syntax

```
RETURN_DATE_TIME_AS_STRING = { ON | OFF }
```



<a name="loioa652ffd684f2101583dcef31685601cf__return_date_time_values1"/>

## Allowed Values

ON, OFF



<a name="loioa652ffd684f2101583dcef31685601cf__return_date_time_default1"/>

## Default

OFF



<a name="loioa652ffd684f2101583dcef31685601cf__return_date_time_priv1"/>

## Privileges

Privilege Category: PUBLIC



### 

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa652ffd684f2101583dcef31685601cf__return_date_time_scope1"/>

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

No



</td>
<td valign="top">

No



</td>
<td valign="top">

No



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



<a name="loioa652ffd684f2101583dcef31685601cf__return_date_time_remarks1"/>

## Remarks

RETURN\_DATE\_TIME\_AS\_STRING indicates whether date, time, and timestamp values are returned to applications as a date or time data type or as a string.

When this option is set to ON, the server converts the date, time, or timestamp value to a string before it is sent to the client in order to preserve the TIMESTAMP\_FORMAT, DATE\_FORMAT, or TIME\_FORMAT option setting.

Interactive SQL automatically turns the RETURN\_DATE\_TIME\_AS\_STRING option ON.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[RETURN_DATE_TIME_AS_STRING Option for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/77c385f40ad1417d8f1ea8ca653456e9.html "Controls how a date, time, or timestamp value is passed to the client application when queried.") :arrow_upper_right:

[DATE\_FORMAT Option for Data Lake Relational Engine](date-format-option-for-data-lake-relational-engine-a632563.md "Sets the format used for dates retrieved from the database.")

[TIME\_FORMAT Option for Data Lake Relational Engine](time-format-option-for-data-lake-relational-engine-a664098.md "Sets the format used for times retrieved from the database.")

[TIMESTAMP\_FORMAT Option for Data Lake Relational Engine](timestamp-format-option-for-data-lake-relational-engine-a664875.md "Sets the format used for timestamps retrieved from the database.")

