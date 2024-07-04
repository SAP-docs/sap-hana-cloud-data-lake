<!-- loio9e5f62ee0d9149c59b4513d19627b8ce -->

# AUTOCOMMIT\_DDL Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Controls whether or not an automatic commit occurs after every DDL transaction.



<a name="loio9e5f62ee0d9149c59b4513d19627b8ce__section_dzz_4jj_kyb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be set when:

-   Connected to SAP HANA database as a SAP HANA database user.
-   Connected directly to data lake Relational Engine **coordinator** as a data lake Relational Engine user



<a name="loio9e5f62ee0d9149c59b4513d19627b8ce__section_vh2_ydk_kxb"/>

## Syntax

```
AUTOCOMMIT_DDL = { ON | OFF };
```



<a name="loio9e5f62ee0d9149c59b4513d19627b8ce__section_hxr_ydk_kxb"/>

## Allowed Values

ON, OFF



<a name="loio9e5f62ee0d9149c59b4513d19627b8ce__section_wdg_zdk_kxb"/>

## Default

ON



<a name="loio9e5f62ee0d9149c59b4513d19627b8ce__section_shs_zdk_kxb"/>

## Privileges

Privilege Category: PUBLIC



### 

The privileges required depend on your data lake Relational Engine \(SAP HANA DB-Managed\) connection method:


<dl>
<dt><b>

Connected to SAP HANA database as a SAP HANA database user:

</b></dt>
<dd>

To set a database option temporarily, use the SET\_TEMPORARY\_OPTION procedure, which requires you be a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.

-   See [SET\_TEMPORARY\_OPTION Procedure for SAP HANA Database](../080-sap-hana-database-for-data-lake-relational-engine/set-temporary-option-procedure-for-sap-hana-database-abcd703.md).




</dd><dt><b>

Connected directly to data lake Relational Engine **coordinator** as a data lake Relational Engine user:

</b></dt>
<dd>

-   Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



</dd>
</dl>



<a name="loio9e5f62ee0d9149c59b4513d19627b8ce__section_k1j_12k_kxb"/>

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



<a name="loio9e5f62ee0d9149c59b4513d19627b8ce__section_vkv_12k_kxb"/>

## Remarks

This option can only be set when you are directly connected to the coordinator. An error is returned if you attempt to set the option when connected to a writer node. The AUTOCOMMIT\_DDL option cannot be set to OFF if the AUTO\_COMMIT option is set to ON. The two options cannot be set in contradiction of each other.

This option can only be set temporarily for the current connection. When you issue the SET TEMPORARY OPTION statement, any uncommitted transactions are automatically committed before the option is set, regardless of whether the option is being enabled or disabled.

**Related Information**  


[Transactional DDL in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2024_3_QRC/en-US/b2cc85f7c63242aca62bf0ee446b6524.html "Transactional DDL lets you execute an arbitrary number of DDL statements as a single transaction and then decide whether to commit or roll back the transaction as a whole.") :arrow_upper_right:

[AUTO\_COMMIT Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)](auto-commit-option-for-data-lake-relational-engine-sap-hana-db-managed-cf5e812.md "Causes an automatic commit after every DML request.")

