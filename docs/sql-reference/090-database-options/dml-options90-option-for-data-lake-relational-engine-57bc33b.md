<!-- loio57bc33b5a1124caa8b117e73bf8b1988 -->

# DML\_OPTIONS90 Option for Data Lake Relational Engine

Controls whether zone maps are used querying to potentially improve performance.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loio57bc33b5a1124caa8b117e73bf8b1988__section_zx3_g24_hrb"/>

## Syntax

```
DML_OPTIONS90 = <value>
```



## Allowed Values

-   0 – production mode. Zone map predicates are considered for query processing by the optimizer.
-   1 – off. Zone map predicates are not used.
-   2 – diagnostic mode. Zone map predicates are created but are validated only; they are not used in the computation of the query’s result.



<a name="loio57bc33b5a1124caa8b117e73bf8b1988__section_mvv_lgw_lcb"/>

## Default

0



<a name="loio57bc33b5a1124caa8b117e73bf8b1988__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loio57bc33b5a1124caa8b117e73bf8b1988__section_csj_mgw_lcb"/>

## Scope

-   Option can be set at the database \(PUBLIC\) or user level. At the database level, the value becomes the default for any new user, but has no impact on existing users. At the user level, overrides the PUBLIC value for that user only. No system privilege is required to set option for self. System privilege is required to set at database level or at user level for any user other than self.

-   Can be set temporary for an individual connection or for the PUBLIC role. Takes effect immediately.




<a name="loio57bc33b5a1124caa8b117e73bf8b1988__section_o4z_ngw_lcb"/>

## Remarks

Requires data lake Relational Engine SP 03 or later.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

