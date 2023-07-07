<!-- loio59327e42f46b461db8a501229bc29461 -->

# GRANT ROLE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Grants roles to users or other roles, with or without administrative rights.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Executing SQL Statements](remote-execute-usage-examples-for-executing-sql-statements-fd99ac0.md).
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
GRANT ROLE <role_name> [, …] 
   TO <grantee> [, …]
   [ {WITH NO ADMIN | WITH ADMIN [ ONLY ] } OPTION ]
   [ WITH NO SYSTEM PRIVILEGE INHERITANCE ]
```

```
<role_name>
   { <user-defined role name>
   | SYS_DL_CUSTOMER_ADMIN_ROLE }
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio59327e42f46b461db8a501229bc29461__section_uk2_mbj_twb"/>

## Parameters


<dl>
<dt><b>

`role_name`

</b></dt>
<dd>

The role must already exist in the database. Separate multiple role names with commas. Although schema do not have passwords associated with them and cannot be used to connect to the database, a security definer procedure owned by a schema is effectively running as if the schema were the user. Therefore, system privileges and roles can be granted to a schema.



</dd><dt><b>

*<grantee\>*

</b></dt>
<dd>

Must be the name of an existing user or role that has a login password, or a schema. If a procedure owned by a schema requires a specific role in order to be executed, then the role must be granted to the schema containing the procedure. Separate multiple user\_IDs with commas.



</dd><dt><b>

WITH NO ADMIN OPTION

</b></dt>
<dd>

Each *<grantee\>* is granted the underlying system privileges of the role, but cannot grant the role to another user.



</dd><dt><b>

WITH ADMIN ONLY OPTION

</b></dt>
<dd>

Each *<userID\>* is granted administrative privileges over each *<role\_name\>*, but not the underlying system privileges of *<role\_name\>*.

This option is not supported with the The SYS\_DL\_CUSTOMER\_ADMIN\_ROLE role.



</dd><dt><b>

WITH ADMIN OPTION

</b></dt>
<dd>

Each userID is granted the underlying system privileges of each *<role\_name\>*, along with the ability to grant *<role\_name\>* to another user.

This option is not supported with the The SYS\_DL\_CUSTOMER\_ADMIN\_ROLE role.



</dd><dt><b>

WITH NO SYSTEM PRIVILEGE INHERITANCE

</b></dt>
<dd>

The underlying system privileges of the granting role are not inherited by the members of the receiving role. However, if the receiving role is a user-extended role, the underlying system privileges are granted to the extended user.

This option is not supported with the The SYS\_DL\_CUSTOMER\_ADMIN\_ROLE role.



</dd>
</dl>



<a name="loio59327e42f46b461db8a501229bc29461__section_zc3_nbj_twb"/>

## Remarks

-   When granted to user-extended roles, the WITH NO SYSTEM PRIVILEGE INHERITANCE clause applies to members of the role only. The user acting as a role automatically inherits the underlying system privileges regardless of the clause.
-   The WITH NO ADMIN OPTION WITH NO SYSTEM PRIVILEGE INHERITANCE and WITH NO SYSTEM PRIVILEGE INHERITANCE clauses are semantically equivalent.
-   The WITH ADMIN OPTION and WITH ADMIN ONLY OPTION clauses are not supported for system roles.

Use of the WITH ADMIN OPTION or WITH ADMIN ONLY OPTION clause allows the grantee to grant or revoke the role, but does not allow the grantee to drop the role.



<a name="loio59327e42f46b461db8a501229bc29461__section_sg3_4bj_twb"/>

## Privileges



### 

The privileges required depend on your data lake Relational Engine \(SAP HANA DB-Managed\) connection method:


<dl>
<dt><b>

Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure:

</b></dt>
<dd>

Requires one of:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



</dd><dt><b>

Connected directly to data lake Relational Engine as a data lake Relational Engine user:

</b></dt>
<dd>

Requires the MANAGE ROLES system privilege.



</dd>
</dl>



<a name="loio59327e42f46b461db8a501229bc29461__section_fc2_pbj_twb"/>

## Standards

-   SQL – other syntaxes are vendor extensions to ISO/ANSI SQL grammar
-   SAP database products – supported by SAP Adaptive Server Enterprise



<a name="loio59327e42f46b461db8a501229bc29461__section_cxq_pbj_twb"/>

## Examples

The following example grants Sales\_Role to Sally, with administrative privileges, which means she can grant or revoke Sales\_Role to other users as well as perform any authorized tasks granted by the role:

```
GRANT ROLE Sales_Role TO Sally WITH ADMIN OPTION
```

**Related Information**  


[REVOKE ROLE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](revoke-role-statement-for-data-lake-relational-engine-sap-hana-db-managed-189a04b.md "Removes a users membership in a role or his or her ability to administer the role.")

[GRANT ROLE Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a3e379cc84f21015bccfaff98164bf01.html "Grants roles to users or other roles, with or without administrative rights.") :arrow_upper_right:

