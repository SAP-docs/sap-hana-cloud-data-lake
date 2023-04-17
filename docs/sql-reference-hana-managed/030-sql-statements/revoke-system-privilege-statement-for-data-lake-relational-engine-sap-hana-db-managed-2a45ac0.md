<!-- loio2a45ac0bacf44b879b464c83767c2f48 -->

# REVOKE System Privilege Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Removes specific system privileges from specific users and the right to administer the privilege.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Executing SQL Statements](remote-execute-usage-examples-for-executing-sql-statements-fd99ac0.md).
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
REVOKE [ ADMIN OPTION FOR ] <system_privilege_name> [,...]
   FROM <user_id> [,...]
```



<a name="loio2a45ac0bacf44b879b464c83767c2f48__section_lrd_xmk_gtb"/>

## Parameters

 ADMIN OPTION FOR
 :   Each *<system\_privilege\>* must currently be granted to each *<user\_id\>* specified with administrative privileges.

    > ### Note:  
    > This clause revokes only the administrative privileges of the system privilege; the system privilege itself remains granted. However, if the system privilege was originally granted with the WITH ADMIN ONLY OPTION clause, the ADMIN OPTION FOR clause completely revokes the system privilege. Under this scenario, use of the ADMIN OPTION FOR clause is not required to revoke administrative privileges.

  *<system\_privilege\_name\>*
 :   Must be an existing system privilege.

  *<user\_id\>*
 :   Must be the name of an existing user or role that has a login password. Separate multiple user\_IDs with commas.

 

<a name="loio2a45ac0bacf44b879b464c83767c2f48__section_gjw_xmk_gtb"/>

## Remarks

Depending on how the system privilege was initially granted, using the ADMIN OPTION FOR clause when revoking a system privilege has different results. If the system privilege was originally granted with the WITH ADMIN OPTION clause, including the ADMIN OPTION FOR clause in the revoke statement revokes only the ability to administer the system privilege \(that is, grant the system privilege to another user\). The ability to actually use the system privilege remains. However, if the system privilege was originally granted with the WITH ADMIN ONLY OPTION clause, including the ADMIN OPTION FOR clause in the revoke statement is semantically equivalent to revoking the entire system privilege.

Finally, if the system privilege was originally grant with the WITH NO ADMIN OPTION clause, and the ADMIN OPTION FOR clause is included in the revoke statement, nothing is revoked because there were no administrative system privileges granted in the first place.



<a name="loio2a45ac0bacf44b879b464c83767c2f48__section_byr_pxy_wwb"/>

## Privileges



### 

The privileges required depend on your data lake Relational Engine \(SAP HANA DB-Managed\) connection method:

 Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure:
 :   You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).

  Connected directly to data lake Relational Engine as a data lake Relational Engine user:
 :   You must have been granted the specific system privilege with administrative privilege.

 

<a name="loio2a45ac0bacf44b879b464c83767c2f48__section_bbn_ymk_gtb"/>

## Standards

-   SQL – other syntaxes are vendor extensions to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise 

**Related Information**  


[GRANT System Privilege Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](grant-system-privilege-statement-for-data-lake-relational-engine-sap-hana-db-managed-c039f62.md "Grants specific system privileges to users or roles, with or without administrative rights.")

