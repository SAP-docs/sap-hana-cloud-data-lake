<!-- loioa426759484f2101583e1ad63a3dfc2e0 -->

# DROP LDAP SERVER Statement for Data Lake Relational Engine

Removes the named LDAP server configuration object from the `SYSLDAPSERVER` system view after verifying that the LDAP server configuration object is not in a READY or ACTIVE state.



<a name="loioa426759484f2101583e1ad63a3dfc2e0__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
DROP LDAP SERVER <ldapua-server-name>
   [ WITH DROP ALL REFERENCES ] [ WITH SUSPEND ]
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa426759484f2101583e1ad63a3dfc2e0__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

WITH DROP ALL REFERENCES

</b></dt>
<dd>

Allows the removal of an LDAP server configuration object from service that has a reference in a login policy.



</dd><dt><b>

WITH SUSPEND

</b></dt>
<dd>

Allows an LDAP server configuration object to be dropped even if in a READY or ACTIVE state.



</dd>
</dl>



<a name="loioa426759484f2101583e1ad63a3dfc2e0__IQ_Usage"/>

## Remarks

The `DROP LDAP SERVER` statement fails when it is issued against an LDAP server configuration object that is in a READY or ACTIVE state. This ensures that an LDAP server configuration object in active use cannot be accidentally dropped.The `DROP LDAP SERVER` statement also fails if a login policy exists with a reference to the LDAP server configuration object.



<a name="loioa426759484f2101583e1ad63a3dfc2e0__IQ_Permissions"/>

## Privileges

Requires the MANAGE ANY LDAP SERVER system privilege.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



<a name="loioa426759484f2101583e1ad63a3dfc2e0__IQ_Standards"/>

## Standards

ANSI SQL – compliance level: Transact-SQL extension



<a name="loioa426759484f2101583e1ad63a3dfc2e0__IQ_Examples"/>

## Examples

In the following example, assuming that references to the LDAP server configuration object have been removed from all login policies, the following two sets of commands are equivalent:

```
DROP LDAP SERVER ldapserver1 WITH DROP ALL REFERENCES WITH SUSPEND;
```

```
ALTER LDAP SERVER ldapserver1 WITH SUSPEND DROP LDAP SERVER ldapserver1 WITH DROP ALL REFERENCES;
```

Using the WITH DROP ALL REFERENCES and WITH SUSPEND parameters eliminates the need to execute an `ALTER LDAP SERVER` statement before the `DROP LDAP SERVER` statement

**Related Information**  


[ALTER LDAP SERVER Statement for Data Lake Relational Engine](alter-ldap-server-statement-for-data-lake-relational-engine-a425eb5.md "Any changes to an LDAP server configuration object are applied on subsequent connections. Any connection already started when the change is applied does not immediately reflect the change.")

[CREATE LDAP SERVER Statement for Data Lake Relational Engine](create-ldap-server-statement-for-data-lake-relational-engine-a424e90.md "Creates a new LDAP server configuration object for LDAP user authentication. Parameters defined during the creation of an LDAP server configuration object are stored in the ISYSLDAPSERVER (system view SYSLDAPSERVER) system table.")

[VALIDATE LDAP SERVER Statement for Data Lake Relational Engine](validate-ldap-server-statement-for-data-lake-relational-engine-a426f91.md "Validates changes to the settings of existing LDAP server configuration objects before applying them.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

