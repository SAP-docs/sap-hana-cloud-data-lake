<!-- loioa632279984f21015b47581522c9e7a93 -->

# DATE\_FIRST\_DAY\_OF\_WEEK Option for Data Lake Relational Engine

Determines the first day of the week.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa632279984f21015b47581522c9e7a93__date_first_day_syntax1"/>

## Syntax

```
DATE_FIRST_DAY_OF_WEEK = { 0 | 1 | 2 | 3 | 4 | 5 | 6 }
```



<a name="loioa632279984f21015b47581522c9e7a93__date_first_day_values1"/>

## Allowed Values

0 to 6



<a name="loioa632279984f21015b47581522c9e7a93__date_first_day_default1"/>

## Default

0 \(Sunday\)



<a name="loioa632279984f21015b47581522c9e7a93__date_first_day_priv1"/>

## Privileges

Privilege Category: PUBLIC



### 

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa632279984f21015b47581522c9e7a93__date_first_day_scope1"/>

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



<a name="loioa632279984f21015b47581522c9e7a93__date_first_day_remarks1"/>

## Remarks

By default, Sunday is day 1, Monday is day 2, Tuesday is day 3, and so on. This option specifies which day is the first day of the week:

-   0 – Sunday
-   1 – Monday
-   2 – Tuesday
-   3 – Wednesday
-   4 – Thursday
-   5 – Friday
-   6 – Saturday

For example, if you change the value of DATE\_FIRST\_DAY\_OF\_WEEK to 3, Wednesday becomes day 1, Thursday becomes day 2, and so on. This option only affects the DOW and DATEPART functions.

The SAP SQL Anywhere option FIRST\_DAY\_OF\_WEEK performs the same function, but assigns the values 1 through 7 instead of 0 through 6. 1 stands for Monday and 7 for Sunday \(the default\).

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[DATE_FIRST_DAY_OF_WEEK Option for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/7b332a76259342ac974c9701abf41265.html "Determines the first day of the week.") :arrow_upper_right:

