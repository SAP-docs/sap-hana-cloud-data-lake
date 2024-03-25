<!-- loioa3eadda384f21015afd5a736a04daab7 -->

# REVOKE System Privilege Statement for Data Lake Relational Engine

Removes specific system privileges from specific users and the right to administer the privilege.



<a name="loioa3eadda384f21015afd5a736a04daab7__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
REVOKE [ ADMIN OPTION FOR ] <system_privilege_name> [,...]
   FROM <user_id> [,...]
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa3eadda384f21015afd5a736a04daab7__revoke_system_priv_parm1"/>

## Parameters


<dl>
<dt><b>

ADMIN OPTION FOR

</b></dt>
<dd>

Each *<system\_privilege\>* must currently be granted to each *<user\_id\>* specified with administrative privileges.

> ### Note:  
> This clause revokes only the administrative privileges of the system privilege; the system privilege itself remains granted. However, if the system privilege was originally granted with the WITH ADMIN ONLY OPTION clause, the ADMIN OPTION FOR clause completely revokes the system privilege. Under this scenario, use of the ADMIN OPTION FOR clause is not required to revoke administrative privileges.



</dd><dt><b>

*<system\_privilege\_name\>*

</b></dt>
<dd>

Must be an existing system privilege.



</dd><dt><b>

*<user\_id\>*

</b></dt>
<dd>

Must be the name of an existing user or role that has a login password. Separate multiple user\_IDs with commas.



</dd>
</dl>



<a name="loioa3eadda384f21015afd5a736a04daab7__revoke_system_priv_remarks1"/>

## Remarks

Depending on how the system privilege was initially granted, using the ADMIN OPTION FOR clause when revoking a system privilege has different results. If the system privilege was originally granted with the WITH ADMIN OPTION clause, including the ADMIN OPTION FOR clause in the revoke statement revokes only the ability to administer the system privilege \(that is, grant the system privilege to another user\). The ability to actually use the system privilege remains. However, if the system privilege was originally granted with the WITH ADMIN ONLY OPTION clause, including the ADMIN OPTION FOR clause in the revoke statement is semantically equivalent to revoking the entire system privilege.

Finally, if the system privilege was originally grant with the WITH NO ADMIN OPTION clause, and the ADMIN OPTION FOR clause is included in the revoke statement, nothing is revoked because there were no administrative system privileges granted in the first place.



<a name="loioa3eadda384f21015afd5a736a04daab7__revoke_system_privileges1"/>

## Privileges



### 

Requires administrative privilege over the system privilege being revoked.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



<a name="loioa3eadda384f21015afd5a736a04daab7__revoke_system_priv_standards1"/>

## Standards

-   SQL – other syntaxes are vendor extensions to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise 

**Related Information**  


[REVOKE Object-Level Privilege Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/f14139fa124d4e5da23c1da6a5009417.html "Removes object-level privileges that were given using the GRANT statement.") :arrow_upper_right:

[REVOKE System Privilege Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/2a45ac0bacf44b879b464c83767c2f48.html "Removes specific system privileges from specific users and the right to administer the privilege.") :arrow_upper_right:

