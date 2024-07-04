<!-- loioa629640a84f21015acf6e96acb7107a7 -->

# Introduction to Database Options

Database options control many aspects of database behavior including compatibility, error handling, and concurrency.

For example, you can use database options for the purposes such as:

-   Error handling – lets you control what happens when errors, such as dividing by zero or overflow errors, occur.
-   Concurrency and transactions – lets you control the degree of concurrency and details of COMMIT behavior using options.

You set options with the SET OPTION statement, which has this general syntax:

```
SET [ EXISTING ] [ TEMPORARY ] OPTION... [ <userid>. | PUBLIC. ]<option-name> = [ <option-value> ];
```

Specify a user ID or role name to set the option only for that user or role. Every user belongs to the PUBLIC role. If no user ID or role is specified, the option change is applied to the currently logged on user ID that issued the SET OPTION statement.

The maximum length of *<option-value\>*, when set to a string, is 127 bytes.

For example, this statement applies a change to the PUBLIC user ID, a role to which all users belong:

```
SET OPTION Public.login_mode = standard;
```

> ### Remember:  
> When you upgrade your data lake instance to a new version, all database options get reset to their default values. Take a backup of [sp\_iqcheckoptions System Procedure for Data Lake Relational Engine](../060-stored-procedures/sp-iqcheckoptions-system-procedure-for-data-lake-relational-engine-a59dae3.md) before performing an upgrade so that you can restore your custom option values once the upgrade completes.

When you set an option to TEMPORARY without specifying a user or role, the new option value takes effect only for the currently logged on user ID that issued the statement, and only for the duration of the connection. When you set an option to TEMPORARY for the PUBLIC role, the change remains in place for as long as the database is running — when the database shuts down, TEMPORARY options for the `PUBLIC` role revert back to their permanent value.

When you set an option without issuing the TEMPORARY keyword, the new option value is permanent for the user or role who issued the statement.

See *Scope and Duration of Database Options*, *Temporary Options*, and *SET OPTION Statement* for more information on temporary versus permanent option values.

> ### Note:  
> For all database options that accept integer values, data lake Relational Engine truncates any decimal *<option-value\>* setting to an integer value. For example, the value 3.8 is truncated to 3.

> ### Caution:  
> Don't change option settings while fetching rows.

**Related Information**  


[Scope and Duration of Database Options](scope-and-duration-of-database-options-a629c37.md "You can set options at three levels of scope: public, user, and temporary.")

[Temporary Options](temporary-options-a629f1e.md "Adding the TEMPORARY keyword to the SET OPTION statement changes the duration of the change.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[sp\_iqcheckoptions System Procedure for Data Lake Relational Engine](../060-stored-procedures/sp-iqcheckoptions-system-procedure-for-data-lake-relational-engine-a59dae3.md "For the connected user, sp_iqcheckoptions displays a list of the current value and the default value of database and server startup options that have been changed from the default.")

