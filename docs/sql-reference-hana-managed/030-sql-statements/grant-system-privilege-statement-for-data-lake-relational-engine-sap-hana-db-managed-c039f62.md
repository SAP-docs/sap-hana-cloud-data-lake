<!-- loioc039f62f0ec349a99f4f2bc016176c8c -->

# GRANT System Privilege Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Grants specific system privileges to users or roles, with or without administrative rights.



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
GRANT <system_privilege_name> [, …]
   TO <grantee> [, …]
   [ { WITH NO ADMIN | WITH ADMIN [ ONLY ] } OPTION ]
```



<a name="loioc039f62f0ec349a99f4f2bc016176c8c__section_zs1_lqj_gtb"/>

## Parameters

 *<system\_privilege\_name\>*
 :   Must be the name of an existing system privilege.

  TO *<grantee\>*
 :   The name of an existing user, immutable role, or schema. Existing users must have login passwords. . Although schema do not have passwords associated with them and cannot be used to connect to the database, a security definer procedure owned by a schema is effectively running as if the schema were the user. Therefore, any system privileges and roles required by the procedure must be granted to the schema in order to run. Separate multiple *<grantee\>* values with commas.

  WITH NO ADMIN OPTION
 :   The grantee can use the system privilege, but cannot grant the system privilege to another user, role or schema.

  WITH ADMIN ONLY OPTION
 :   The grantee can grant the system privilege to another user, role or schema but cannot use the system privilege itself.

  WITH ADMIN OPTION
 :   The grantee can use the system privilege and grant the system privilege to another user, role or schema.

 

<a name="loioc039f62f0ec349a99f4f2bc016176c8c__section_fxm_4qj_gtb"/>

## Remarks

By default, if no administrative clause is specified in the grant statement, the WITH NO ADMIN OPTION clause is used.



<a name="loioc039f62f0ec349a99f4f2bc016176c8c__section_r4j_tcy_wwb"/>

## Privileges



### 

The privileges required depend on your data lake Relational Engine \(SAP HANA DB-Managed\) connection method:

 Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure:
 :   You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).

  Connected directly to data lake Relational Engine as a data lake Relational Engine user:
 :   You must have been granted the specific system privilege with administrative privilege.

 

<a name="loioc039f62f0ec349a99f4f2bc016176c8c__section_asc_rqj_gtb"/>

## Standards

-   SQL – other syntaxes are vendor extensions to ISO/ANSI SQL grammar



<a name="loioc039f62f0ec349a99f4f2bc016176c8c__IQ_Examples"/>

## Examples

This example grants the ALTER ANY PROCEDURE system privilege to `Sally` with no administrative privileges:

```
GRANT ALTER ANY PROCEDURE TO Sally WITH NO ADMIN OPTION
```

**Related Information**  


[REVOKE System Privilege Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](revoke-system-privilege-statement-for-data-lake-relational-engine-sap-hana-db-managed-2a45ac0.md "Removes specific system privileges from specific users and the right to administer the privilege.")

