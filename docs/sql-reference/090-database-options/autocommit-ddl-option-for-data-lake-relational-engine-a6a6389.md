<!-- loioa6a63898efe04a6181f623fdee447143 -->

# AUTOCOMMIT\_DDL Option for Data Lake Relational Engine

Controls whether or not an automatic commit occurs after every DDL transaction.



<a name="loioa6a63898efe04a6181f623fdee447143__section_d3p_24q_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine **coordinator** as a data lake Relational Engine user.



<a name="loioa6a63898efe04a6181f623fdee447143__autocommit_ddl_syntax1"/>

## Syntax

```
AUTOCOMMIT_DDL = { ON | OFF };
```



<a name="loioa6a63898efe04a6181f623fdee447143__autocommit_ddl_values1"/>

## Allowed Values

ON, OFF



<a name="loioa6a63898efe04a6181f623fdee447143__autocommit_ddl_default1"/>

## Default

ON



<a name="loioa6a63898efe04a6181f623fdee447143__autocommit_ddl_priv1"/>

## Privileges

Privilege Category: PUBLIC



### 

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa6a63898efe04a6181f623fdee447143__autocommit_ddl_scope1"/>

## Scope


<table>
<tr>
<th valign="top">

 

</th>
<th valign="top">

PUBLIC role

</th>
<th valign="top">

For current user

</th>
<th valign="top">

For other users

</th>
</tr>
<tr>
<td valign="top">

Allowed to set permanently?

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

Allowed to set temporarily?

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes \(current connection only\)

</td>
<td valign="top">

No

</td>
</tr>
</table>



<a name="loioa6a63898efe04a6181f623fdee447143__section_v53_ngm_gxb"/>

## Remarks

This option can only be set when you are directly connected to the coordinator. An error is returned if you attempt to set the option when connected to a writer node. The AUTOCOMMIT\_DDL option cannot be set to OFF if the AUTO\_COMMIT option is set to ON. The two options cannot be set in contradiction of each other.

This option can only be set temporarily for the current connection. When you issue the SET TEMPORARY OPTION statement, any uncommitted transactions are automatically committed before the option is set, regardless of whether the option is being enabled or disabled.

**Related Information**  


[Transactional DDL in Data Lake Relational Engine](https://help.sap.com/viewer/a8937bea84f21015a80bc776cf758d50/2024_1_QRC/en-US/6fd1d28ae2324096a609e89e18a1ab57.html "Transactional DDL lets you execute an arbitrary number of DDL statements as a single transaction and then decide whether to commit or roll back the transaction as a whole.") :arrow_upper_right:

[AUTO\_COMMIT Option for Data Lake Relational Engine](auto-commit-option-for-data-lake-relational-engine-fdb9c1e.md "Causes an automatic commit after every DML request.")

