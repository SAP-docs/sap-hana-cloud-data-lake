<!-- loioa874045684f21015abbbd6b7d63613e5 -->

# FP\_NBIT\_ENFORCE\_LIMITS Option for Data Lake Relational Engine

Enforces sizing limits for explicit and implicit NBit columns.



<a name="loioa874045684f21015abbbd6b7d63613e5__section_e4v_wqq_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa874045684f21015abbbd6b7d63613e5__fp_nbit_enforce_limits_syntax1"/>

## Syntax

```
FP_NBIT_ENFORCE_LIMITS = { ON | OFF }
```



<a name="loioa874045684f21015abbbd6b7d63613e5__fp_nbit_enforce_limits_values1"/>

## Allowed Values

ON, OFF



<a name="loioa874045684f21015abbbd6b7d63613e5__fp_nbit_enforce_limits_defaults1"/>

## Default

OFF



<a name="loioa874045684f21015abbbd6b7d63613e5__fp_nbit_enforce_priv1"/>

## Privileges

Privilege Category: PUBLIC



### 

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa874045684f21015abbbd6b7d63613e5__fp_nbit_enforce_limits_scope1"/>

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



## Dependencies

FP\_NBIT\_ENFORCE\_LIMITS applies to databases running where FP\_NBIT\_IQ15\_COMPATIBILITY is set to OFF. If set to ON, the database engine ignores this option.



## Remarks



### 

DML operations check the FP\_NBIT\_ENFORCE\_LIMITS option when the number of distinct values in a column exceeds the explicit limit set in an IQ UNIQUE constraint, which is above the FP\_NBIT\_AUTOSIZE value, or when the dictionary size for an implicit NBit rollover exceeds the FP\_NBIT\_ROLLOVER\_MAX\_MB limit.

If FP\_NBIT\_ENFORCE\_LIMITS is set to:

-   ON – the DML operation throws an error and rolls back
-   OFF – the DML operation continues and the NBit dictionary limits are ignored



`sp_iqindexmetadata` returns details about `Flat FP` or `NBit FP` columns. `sp_iqrebuildindex` can change explicit or implicit `NBit FP` column limits, or reformat the default column index as `Flat FP` or `NBit FP`.

Using sp\_iqrebuildindex to increase the number of distinct values beyond current limits for a Flat FP column when FP\_NBIT\_ENFORCE\_LIMITS is set to ON, returns an error. If FP\_NBIT\_ENFORCE\_LIMITS is OFF, sp\_iqrebuildindex rebuilds the index to the maximum token, which is the largest distinct value.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[FP_NBIT_ENFORCE_LIMITS Option for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/2e6a10d296ec4bd6a7209e65e0171171.html "Enforces sizing limits for explicit and implicit NBit columns.") :arrow_upper_right:

[FP\_NBIT\_AUTOSIZE\_LIMIT Option for Data Lake Relational Engine](fp-nbit-autosize-limit-option-for-data-lake-relational-engine-a873755.md "Limits the number of distinct values in columns that implicitly load as NBit FP.")

[FP\_NBIT\_IQ15\_COMPATIBILITY Option for Data Lake Relational Engine](fp-nbit-iq15-compatibility-option-for-data-lake-relational-engine-a874375.md "Provides support for tokenized FP indexes similar to that available in data lake Relational Engine.")

[FP\_NBIT\_LOOKUP\_MB Option for Data Lake Relational Engine](fp-nbit-lookup-mb-option-for-data-lake-relational-engine-a873a52.md "Limits the total dictionary size per column for implicit NBit FP columns.")

[FP\_NBIT\_ROLLOVER\_MAX\_MB Option for Data Lake Relational Engine](fp-nbit-rollover-max-mb-option-for-data-lake-relational-engine-a873d4b.md "Sets a threshold for the total dictionary size for implicit NBit rollovers to Flat FP.")

[sp\_iqrebuildindex Procedure for Data Lake Relational Engine](../060-stored-procedures/sp-iqrebuildindex-procedure-for-data-lake-relational-engine-a5b342e.md "Rebuilds column indexes.")

[sp\_iqindexmetadata Procedure for Data Lake Relational Engine](../060-stored-procedures/sp-iqindexmetadata-procedure-for-data-lake-relational-engine-a5ad0e4.md "Displays index metadata for a given index.")

