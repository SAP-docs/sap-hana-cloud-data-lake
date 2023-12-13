<!-- loio189a04b4a6cb4098bebcc34f16a78afb -->

# REVOKE ROLE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Removes a users membership in a role or his or her ability to administer the role.



<a name="loio189a04b4a6cb4098bebcc34f16a78afb__section_f2c_11g_xwb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:

-   Connected to SAP HANA database as a SAP HANA database user and using the SAP HANA database REMOTE\_EXECUTE procedure.
-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
REVOKE [ { EXERCISE | ADMIN } OPTION FOR ] ROLE <user-defined-role> 
FROM { <system-role> | <user_id> } [, ...];
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio189a04b4a6cb4098bebcc34f16a78afb__section_lvp_wcj_twb"/>

## Parameters


<dl>
<dt><b>

*<user-defined-role\>*

</b></dt>
<dd>

Must already exist in the database. Separate multiple role names with commas.



</dd><dt><b>

*<user\_id\>*

</b></dt>
<dd>

Must be the name of an existing user or role that has a login password. Separate multiple user\_IDs with commas.



</dd><dt><b>

\{ EXERCISE | ADMIN \} OPTION FOR

</b></dt>
<dd>

Specify the ADMIN OPTION FOR clause to revoke administration rights for the role, but leave exercise rights. Specify the EXERCISE OPTION FOR clause to revoke exercise rights for the role, but leave administration rights. If the clause is not specified, both rights are revoked.



</dd>
</dl>



<a name="loio189a04b4a6cb4098bebcc34f16a78afb__section_igk_xcj_twb"/>

## Remarks

If a role that is being revoked was not granted to *<grantee\>*, then the statement does nothing, and does not return an error.

REVOKE ROLE fails with an error if, as a consequence of executing the statement, the number of administrators for the role being revoked would fall below the required minimum as set by the min\_role\_admins database option.

When revoking a role from the MANAGE ROLES system privilege, you must use the special internal representation SYS\_MANAGE\_ROLES\_ROLE. For example, REVOKE ROLE *<user-defined role name\>* FROM SYS\_MANAGE\_ROLES\_ROLE.



<a name="loio189a04b4a6cb4098bebcc34f16a78afb__section_ckd_ycj_twb"/>

## Privileges



### 

The privileges required depend on your data lake Relational Engine \(SAP HANA DB-Managed\) connection method:


<dl>
<dt><b>

Connected to SAP HANA database as a SAP HANA database user and using the SAP HANA database REMOTE\_EXECUTE procedure:

</b></dt>
<dd>

Requires one of:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the SAP HANA database REMOTE\_EXECUTE procedure associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).

-   See [REMOTE\_EXECUTE Guidance and Examples for Executing SQL Statements](remote-execute-guidance-and-examples-for-executing-sql-statements-fd99ac0.md).




</dd><dt><b>

Connected directly to data lake Relational Engine as a data lake Relational Engine user:

</b></dt>
<dd>

-   Requires the MANAGE ROLES system privilege.



</dd>
</dl>



<a name="loio189a04b4a6cb4098bebcc34f16a78afb__section_npx_ycj_twb"/>

## Standards

SQL – not in the ISO/ANSI SQL standard



<a name="loio189a04b4a6cb4098bebcc34f16a78afb__section_gp4_zcj_twb"/>

## Examples

The following example revokes the user-defined role role1 from user1. Once revoked, user1 no longer has the rights to perform any authorized tasks using any system privileges granted to `role1`.

```
REVOKE ROLE role1 FROM user1;
```

**Related Information**  


[GRANT ROLE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](grant-role-statement-for-data-lake-relational-engine-sap-hana-db-managed-59327e4.md "Grants roles to users or other roles, with or without administrative rights.")

[REVOKE ROLE Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/a3e9de3284f21015bfd7b663b9989fe3.html "Removes a users membership in a role or his or her ability to administer the role.") :arrow_upper_right:

