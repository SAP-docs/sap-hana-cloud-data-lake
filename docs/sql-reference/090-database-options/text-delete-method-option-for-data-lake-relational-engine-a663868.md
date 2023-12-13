<!-- loioa663868b84f21015a23cbc124262f0e9 -->

# TEXT\_DELETE\_METHOD Option for Data Lake Relational Engine

Specifies the algorithm used during a delete in a TEXT index.



<a name="loioa663868b84f21015a23cbc124262f0e9__section_d3p_24q_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa663868b84f21015a23cbc124262f0e9__section_zx3_g24_hrb"/>

## Syntax

```
TEXT_DELETE_METHOD = <value>;
```



## Allowed Values

0 to 2



## Default

0



<a name="loioa663868b84f21015a23cbc124262f0e9__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



## Scope

-   Option can be set at the database \(PUBLIC\) or user level. At the database level, the value becomes the default for any new user, but has no impact on existing users. At the user level, overrides the PUBLIC value for that user only. No system privilege is required to set option for self. System privilege is required to set at database level or at user level for any user other than self.

-   Can be set temporary for an individual connection or for the PUBLIC role. Takes effect immediately.


**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

