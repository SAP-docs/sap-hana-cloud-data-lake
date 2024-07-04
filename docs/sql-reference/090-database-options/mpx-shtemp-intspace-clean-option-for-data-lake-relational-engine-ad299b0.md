<!-- loioad299b0c32d94b3580bd9589cfef1dcc -->

# MPX\_SHTEMP\_INTSPACE\_CLEAN Option for Data Lake Relational Engine

Instructs worker nodes to release all unused shared temporary dbspace memory block allocation units from the allocation unit chain \(with the exception of the first allocation unit\). This cleans the shared temporary dbspace, freeing memory for other queries in your multiplex.



<a name="loioad299b0c32d94b3580bd9589cfef1dcc__section_d3p_24q_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioad299b0c32d94b3580bd9589cfef1dcc__section_ftt_dws_lrb"/>

## Syntax

```
MPX_SHTEMP_INTSPACE_CLEAN = { ON | OFF };
```



## Allowed Values

ON | OFF



<a name="loioad299b0c32d94b3580bd9589cfef1dcc__section_eh5_5ss_tgb"/>

## Default

OFF



<a name="loioad299b0c32d94b3580bd9589cfef1dcc__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: SYSTEM

Requires the SET ANY CUSTOMER SYSTEM OPTION system privilege to set this database option.



<a name="loioad299b0c32d94b3580bd9589cfef1dcc__section_ws1_vss_tgb"/>

## Scope

-   Option can be set at the database \(PUBLIC\) level only.



<a name="loioad299b0c32d94b3580bd9589cfef1dcc__section_xqb_vss_tgb"/>

## Remarks

Shared temporary space is reserved for each node in the multiplex on demand. Space is reserved for a node in an allocation unit. Nodes can have multiple allocation units reserved based on their dynamic space demands. Allocation units are leased to allow nodes to use more space as needed and return the space to a global pool when not needed. Allocation units expire when space usage decreases and their lease time ends, or when a server shuts down.

You can set this option on either the coordinator or a worker node, but SAP recommends you set it on the coordinator node.

When set to ON, MPX\_SHTEMP\_INTSPACE\_CLEAN changes all intermediate unallocated allocation units in the shared temporary dbspace from status ACTIVE to status EXPIRED, with the exception of the first unit in the allocation chain. This frees unused memory allocation units and returns them to the global pool. Freeing shared temporary dbspace memory can improve multiplex performance.

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[sp\_iqsharedtempdistrib System Procedure for Data Lake Relational Engine](../060-stored-procedures/sp-iqsharedtempdistrib-system-procedure-for-data-lake-relational-engine-a23b73a.md "Shows the current shared temp space usage distribution. If run from the coordinator, sp_iqsharedtempdistrib displays shared temp space distribution for all nodes. If run from a worker node, displays shared temp space usage for only that node.")

