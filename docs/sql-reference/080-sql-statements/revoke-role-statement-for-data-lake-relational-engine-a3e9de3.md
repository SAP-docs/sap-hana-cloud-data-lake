<!-- loioa3e9de3284f21015bfd7b663b9989fe3 -->

# REVOKE ROLE Statement for Data Lake Relational Engine

Removes a users membership in a role or his or her ability to administer the role.



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
REVOKE [ { EXERCISE | ADMIN } OPTION FOR ] ROLE <user-defined-role> 
FROM { <system-role> | <user_id> } [, ...]
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa3e9de3284f21015bfd7b663b9989fe3__revoke_role_param1"/>

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



<a name="loioa3e9de3284f21015bfd7b663b9989fe3__revoke_role_remarks1"/>

## Remarks

If a role that is being revoked was not granted to *<grantee\>*, then the statement does nothing, and does not return an error.

REVOKE ROLE fails with an error if, as a consequence of executing the statement, the number of administrators for the role being revoked would fall below the required minimum as set by the min\_role\_admins database option.

When revoking a role from the MANAGE ROLES system privilege, you must use the special internal representation SYS\_MANAGE\_ROLES\_ROLE. For example, REVOKE ROLE *<user-defined role name\>* FROM SYS\_MANAGE\_ROLES\_ROLE.



<a name="loioa3e9de3284f21015bfd7b663b9989fe3__revoke_role_privilege1"/>

## Privileges



### 

To revoke the following roles requires the MANAGE ROLES system privilege.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



<a name="loioa3e9de3284f21015bfd7b663b9989fe3__revoke_role_standards1"/>

## Standards

SQL – not in the ISO/ANSI SQL standard



<a name="loioa3e9de3284f21015bfd7b663b9989fe3__revoke_role_examples1"/>

## Examples

The following example revokes the user-defined role role1 from user1. Once revoked, user1 no longer has the rights to perform any authorized tasks using any system privileges granted to `role1`.

```
REVOKE ROLE role1 FROM user1;
```

**Related Information**  


[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT ROLE Statement for Data Lake Relational Engine](grant-role-statement-for-data-lake-relational-engine-a3e379c.md "Grants roles to users or other roles, with or without administrative rights.")

[REVOKE ROLE Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/189a04b4a6cb4098bebcc34f16a78afb.html "Removes a users membership in a role or his or her ability to administer the role.") :arrow_upper_right:

