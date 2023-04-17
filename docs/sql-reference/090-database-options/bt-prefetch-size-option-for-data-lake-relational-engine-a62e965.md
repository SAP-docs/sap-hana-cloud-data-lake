<!-- loioa62e965884f21015a56fc667d1720a8f -->

# BT\_PREFETCH\_SIZE Option for Data Lake Relational Engine

Restricts the size of the read-ahead buffer for the High\_Group B-tree.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa62e965884f21015a56fc667d1720a8f__section_xdr_2ry_brb"/>

## Syntax

```
BT_PREFETCH_SIZE = <value>
```



<a name="loioa62e965884f21015a56fc667d1720a8f__iq_refso_379"/>

## Allowed Values

0 to 100



<a name="loioa62e965884f21015a56fc667d1720a8f__iq_refso_380"/>

## Default

10



<a name="loioa62e965884f21015a56fc667d1720a8f__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa62e965884f21015a56fc667d1720a8f__iq_refso_381"/>

## Scope

-   Option can be set at the database \(PUBLIC\) or user level. At the database level, the value becomes the default for any new user, but has no impact on existing users. At the user level, overrides the PUBLIC value for that user only. No system privilege is required to set option for self. System privilege is required to set at database level or at user level for any user other than self.

-   Can be set temporary for an individual connection or for the PUBLIC role. Takes effect immediately.




<a name="loioa62e965884f21015a56fc667d1720a8f__iq_refso_382"/>

## Remarks

Setting the value to 0 disables B-tree prefetch.

B-tree prefetch is activated by default for any sequential access to the High\_Group index such as INSERT, large DELETE, range predicates, and DBCC \(Database Consistency Checker\) commands.

BT\_PREFETCH\_SIZE limits the size of the read-ahead buffer for B-tree pages. Reducing prefetch size frees buffers, but also degrades performance at some point. Increasing prefetch size might have marginal returns. This option should be used in conjunction with the options PREFETCH\_GARRAY\_PERCENT, GARRAY\_INSERT\_PREFETCH\_SIZE, and GARRAY\_RO\_PREFETCH\_SIZE for non-unique High\_Group indexes.

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[GARRAY\_INSERT\_PREFETCH\_SIZE Option for Data Lake Relational Engine](garray-insert-prefetch-size-option-for-data-lake-relational-engine-a63762f.md "Specifies number of pages used for prefetch.")

[GARRAY\_RO\_PREFETCH\_SIZE Option for Data Lake Relational Engine](garray-ro-prefetch-size-option-for-data-lake-relational-engine-a637c5e.md "Specifies number of pages used for prefetch.")

[PREFETCH\_GARRAY\_PERCENT Option for Data Lake Relational Engine](prefetch-garray-percent-option-for-data-lake-relational-engine-a64ab57.md "Specifies the percent of prefetch resources designated for performing all DML operations (insert, update, delete, query) on HG indexes.")

[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

