<!-- loioa6462f5f84f21015a40dd5e7b750d63d -->

# ON\_ERROR Option \[Interactive SQL\] for Data Lake Relational Engine

Controls the action taken if an error is encountered while executing statements in Interactive SQL.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa6462f5f84f21015a40dd5e7b750d63d__section_zx3_g24_hrb"/>

## Syntax

```
ON_ERROR = <value>
```



<a name="loioa6462f5f84f21015a40dd5e7b750d63d__iq_refso_817"/>

## Allowed Values

-   STOP – Interactive SQL stops executing statements from the file and returns to the statement window for input.
-   PROMPT – Interactive SQL prompts the user whether to continue.
-   CONTINUE – errors appear in the Messages pane, and Interactive SQL continues executing statements.
-   EXIT – Interactive SQL terminates.
-   NOTIFY\_CONTINUE – the error is reported, and the user is prompted to continue.
-   NOTIFY\_STOP – the error is reported, and the user is prompted to stop executing statements.
-   NOTIFY\_EXIT – the error is reported, and the user is prompted to terminate Interactive SQL.



<a name="loioa6462f5f84f21015a40dd5e7b750d63d__iq_refso_818"/>

## Default

PROMPT



<a name="loioa6462f5f84f21015a40dd5e7b750d63d__section_kdj_f4g_kqb"/>

## Privileges

None



<a name="loioa6462f5f84f21015a40dd5e7b750d63d__iq_refso_819"/>

## Remarks

Controls the action taken, if an error is encountered while executing statements. When you are executing a `.SQL` file, the values STOP and EXIT are equivalent.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

