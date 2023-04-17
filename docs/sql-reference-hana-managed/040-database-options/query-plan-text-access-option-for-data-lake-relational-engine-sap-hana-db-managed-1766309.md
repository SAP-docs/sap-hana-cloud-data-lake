<!-- loio176630977a7d4a46b04fe1f7b30fd9c2 -->

# QUERY\_PLAN\_TEXT\_ACCESS Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Enables or prevents users from accessing query plans from the Interactive SQL client or from using SQL functions to get plans.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Setting Database Options](remote-execute-usage-examples-for-setting-database-options-0023bea.md).



<a name="loio176630977a7d4a46b04fe1f7b30fd9c2__section_kd4_v2t_lrb"/>

## Syntax

```
QUERY_PLAN_TEXT_ACCESS = { ON | OFF }
```



<a name="loio176630977a7d4a46b04fe1f7b30fd9c2__section_bdy_v2t_lrb"/>

## Allowed Values

ON, OFF



<a name="loio176630977a7d4a46b04fe1f7b30fd9c2__section_fqm_w2t_lrb"/>

## Default

OFF



<a name="loio176630977a7d4a46b04fe1f7b30fd9c2__section_q1s_vrb_dxb"/>

## Privileges

Privilege Category: SYSTEM



### 

You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loio176630977a7d4a46b04fe1f7b30fd9c2__section_oyh_1ft_lrb"/>

## Scope

-   Option can be set at the database \(PUBLIC\) or user level. At the database level, the value becomes the default for any new user, but has no impact on existing users. At the user level, overrides the PUBLIC value for that user only. No system privilege is required to set option for self. System privilege is required to set at database level or at user level for any user other than self.

-   Can be set temporary for an individual connection or for the PUBLIC role. Takes effect immediately.




<a name="loio176630977a7d4a46b04fe1f7b30fd9c2__section_rx5_cft_lrb"/>

## Remarks

When QUERY\_PLAN\_TEXT\_ACCESS option is ON, users can view, save, and print query plans from the Interactive SQL client. When the option is OFF, query plans are not cached, and other query plan-related database options have no effect on the query plan that is shown from the Interactive SQL client. This error message appears:

```
No plan available. The database option QUERY_PLAN_TEXT_ACCESS is OFF.
```

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[QUERY\_PLAN\_TEXT\_CACHING Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)](query-plan-text-caching-option-for-data-lake-relational-engine-sap-hana-db-managed-bee56c4.md "Allows you to specify whether or not data lake Relational Engine generates and caches IQ plans for queries executed by the user.")

[QUERY_PLAN_TEXT_ACCESS Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a64f443284f21015acbbd8e919d9c49b.html "Enables or prevents users from accessing query plans from the Interactive SQL client or from using SQL functions to get plans.") :arrow_upper_right:

