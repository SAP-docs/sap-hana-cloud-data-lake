<!-- loioa63b556984f21015b722b43d1bfa98ce -->

# JOIN\_EXPANSION\_FACTOR Option for Data Lake Relational Engine

Controls how conservative the optimizer’s join result estimates are in unusually complex situations.



> ### Restriction:  
> This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa63b556984f21015b722b43d1bfa98ce__iq_refso_660"/>

## Default

30



<a name="loioa63b556984f21015b722b43d1bfa98ce__iq_refso_662"/>

## Remarks

This option controls how conservative the join optimizer’s result size estimates are in situations where an input to a specific join has already passed through at least one intermediate join that can result in multiple copies of rows projected from the table being joined.

A level of zero indicates that the optimizer should use the same estimation method above intermediate expanding joins as it would if there were no intermediate expanding joins.

This results in the most aggressive \(small\) join result size estimates.

A level of 100 indicates that the optimizer should be much more conservative in its estimates whenever there are intermediate expanding joins, and this results in the most conservative \(large\) join result size estimates.

Normally, you should not need to change this value. If you do, set JOIN\_EXPANSION\_FACTOR as a temporary or user option.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

