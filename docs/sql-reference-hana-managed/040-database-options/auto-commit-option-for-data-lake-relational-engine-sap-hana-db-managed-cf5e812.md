<!-- loiocf5e8122bf4744e0a5b12fce237fec00 -->

# AUTO\_COMMIT Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Causes an automatic commit after every DML request.



<a name="loiocf5e8122bf4744e0a5b12fce237fec00__section_dzz_4jj_kyb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be set when:

-   Connected to SAP HANA database as a SAP HANA database user and using the SAP HANA database REMOTE\_EXECUTE\_DDL procedure.
-   Connected directly to data lake Relational Engine **coordinator** as a data lake Relational Engine user



<a name="loiocf5e8122bf4744e0a5b12fce237fec00__section_bpg_whk_kxb"/>

## Default

OFF



<a name="loiocf5e8122bf4744e0a5b12fce237fec00__section_yzx_whk_kxb"/>

## Privileges

Privilege Category: PUBLIC



### 



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



<a name="loiocf5e8122bf4744e0a5b12fce237fec00__section_y5k_yhk_kxb"/>

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



<a name="loiocf5e8122bf4744e0a5b12fce237fec00__section_rjc_zhk_kxb"/>

## Remarks

If this option is set to On, then the database server automatically commits after every DML request. This option can only be set temporarily for a connection.

The AUTO\_COMMIT option cannot be set to ON if the AUTOCOMMIT\_DDL is currently set to OFF as these two options are contradictory.

> ### Note:  
> The AUTO\_COMMIT option is different from the chained option. Setting AUTO\_COMMIT to On forces the database server to commit after every request. Setting the CHAINED option to Off forces the database server to commit after each statement. This distinction is most important when executing a stored procedure. Setting the CHAINED option to Off results in a commit request after the execution of each individual statement within the procedure. Setting the AUTO\_COMMIT option to On results in a single commit request once the entire procedure finishes executing. In cases where automatic commit is necessary, it is much better to use the AUTO\_COMMIT option rather than the CHAINED option.

**Related Information**  


[AUTOCOMMIT\_DDL Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)](autocommit-ddl-option-for-data-lake-relational-engine-sap-hana-db-managed-9e5f62e.md "Controls whether or not an automatic commit occurs after every DDL transaction.")

