<!-- loioa66588f484f21015814ea5ee2686d57e -->

# TRIM\_PARTIAL\_MBC Option for Data Lake Relational Engine

Allows automatic trimming of partial multibyte character data.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa66588f484f21015814ea5ee2686d57e__section_kng_drh_mrb"/>

## Syntax

```
TRIM_PARTIAL_MBC = { ON | OFF }
```



<a name="loioa66588f484f21015814ea5ee2686d57e__iq_refso_1064"/>

## Allowed Values

ON, OFF



<a name="loioa66588f484f21015814ea5ee2686d57e__iq_refso_1065"/>

## Default

OFF



<a name="loioa66588f484f21015814ea5ee2686d57e__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: SYSTEM

Requires the SET ANY CUSTOMER SYSTEM OPTION system privilege to set this database option.



<a name="loioa66588f484f21015814ea5ee2686d57e__iq_refso_1066"/>

## Scope

-   Option can be set at the database \(PUBLIC\) level only.

-   Takes effect immediately.




<a name="loioa66588f484f21015814ea5ee2686d57e__iq_refso_1067"/>

## Remarks

Provides consistent loading of data for collations that contain both single-byte and multibyte characters. When TRIM\_PARTIAL\_MBC is ON:

-   A partial multibyte character is replaced with a blank when loading into a CHAR column.
-   A partial multibyte character is truncated when loading into a VARCHAR column.

When TRIM\_PARTIAL\_MBC is OFF, normal CONVERSION\_ERROR semantics are in effect.

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[CONVERSION\_ERROR Option \[TSQL\] for Data Lake Relational Engine](conversion-error-option-tsql-for-data-lake-relational-engine-a63018a.md "Controls reporting of data type conversion failures on fetching information from the database.")

[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

