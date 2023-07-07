<!-- loio1ef5b722034040b99df6c8d44a5e93e8 -->

# REVOKE Statement for SAP HANA Database

Revoke privileges from users and roles to remove the ability to manage and query data lake Relational Engine data.



<a name="loio1ef5b722034040b99df6c8d44a5e93e8__sql_revoke_1sql_revoke_syntax"/>

## Syntax

```
REVOKE <system_privilege> [,...] FROM <grantee>
 | REVOKE <schema_privilege> [,...] ON SCHEMA <hana_relational_container_schema_name> FROM <grantee>
 | REVOKE <object_privilege> [,...] ON <hana_relational_container_schema_name>.<hana_object_name> FROM <grantee>
 | REVOKE <role_name> [,...] FROM <grantee>
 | REVOKE EXECUTE ON <relational_container_name>.REMOTE_EXECUTE FROM <relational_container_name>
 | REVOKE { CREATE VIRTUAL TABLE | REMOTE TABLE ADMIN } ON REMOTE SOURCE SYSHDL_<relational_container_name>_SOURCE FROM <grantee>
```



<a name="loio1ef5b722034040b99df6c8d44a5e93e8__sql_revoke_1sql_revoke_syntax_elements"/>

## Syntax Elements

For the definitions of available syntax elements and privileges, see the GRANT statement.



<a name="loio1ef5b722034040b99df6c8d44a5e93e8__sql_grant_1sql_grant_description"/>

## Description

This syntax is specific to revoking SAP HANA database privileges in a data lake Relational Engine context. For additional non-data lake Relational Engine specific syntax , see the *REVOKING Statement \(Access Control\)* in the *SAP HANA Cloud, SAP HANA Database SQL Reference Guide*.



<a name="loio1ef5b722034040b99df6c8d44a5e93e8__section_jb3_ktc_pbb"/>

## Permissions

For users without the ROLE ADMIN system privilege, only the user that granted a specific privilege can revoke it.



<a name="loio1ef5b722034040b99df6c8d44a5e93e8__section_tmt_qvy_ddb"/>

## Description

If a user has been granted a role, then you can’t revoke a subset of the privileges belonging to that role. To grant a subset of privileges contained within a role, revoke the entire role and grant the required privileges separately. For users without ROLE ADMIN privileges, only the user that granted a specific privilege can revoke it.

Revoking a privilege or role can lead to some views becoming inaccessible or procedures that the user can no longer execute. This situation occurs if a view or procedure depends on a revoked privilege or on one of the privileges the role had.

Revoking a privilege that had been granted with WITH GRANT OPTION or with WITH ADMIN OPTION results in recursive revocation of privileges. Privileges aren’t only revoked from the user specified in the command, but also from all the users and roles that were granted that privilege directly or indirectly by the specified user.

Privileges can be granted to a user or role by more than one grantor; revocation of a privilege by one grantor doesn’t necessarily mean that the privilege is revoked from the user or role.

**Related Information**  


[GRANT Statement for SAP HANA Database](grant-statement-for-sap-hana-database-ee1648d.md "Grant privileges to users and roles to manage and query data lake Relational Engine data.")

[SAP HANA Cloud, SAP HANA Database SQL Reference Guide](https://help.sap.com/viewer/c1d3f60099654ecfb3fe36ac93c121bb/cloud/en-US)

