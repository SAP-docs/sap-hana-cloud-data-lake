<!-- loioa3dfcb0284f21015b74ac3cded42ee69 -->

# GRANT System Privilege Statement for Data Lake Relational Engine

Grants specific system privileges to users or roles, with or without administrative rights.



<a name="loioa3dfcb0284f21015b74ac3cded42ee69__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
GRANT <system_privilege_name> [, …]
   TO <grantee> [, …]
   [ { WITH NO ADMIN | WITH ADMIN [ ONLY ] } OPTION ]
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa3dfcb0284f21015b74ac3cded42ee69__grant_system_priv_parm1"/>

## Parameters


<dl>
<dt><b>

*<system\_privilege\_name\>*

</b></dt>
<dd>

Must be the name of an existing system privilege.



</dd><dt><b>

TO *<grantee\>*

</b></dt>
<dd>

The name of an existing user, immutable role, or schema. Existing users must have login passwords. . Although schema do not have passwords associated with them and cannot be used to connect to the database, a security definer procedure owned by a schema is effectively running as if the schema were the user. Therefore, any system privileges and roles required by the procedure must be granted to the schema in order to run. Separate multiple *<grantee\>* values with commas.



</dd><dt><b>

WITH NO ADMIN OPTION

</b></dt>
<dd>

The grantee can use the system privilege, but cannot grant the system privilege to another user, role or schema.



</dd><dt><b>

WITH ADMIN ONLY OPTION

</b></dt>
<dd>

The grantee can grant the system privilege to another user, role or schema but cannot use the system privilege itself.



</dd><dt><b>

WITH ADMIN OPTION

</b></dt>
<dd>

The grantee can use the system privilege and grant the system privilege to another user, role or schema.



</dd>
</dl>



<a name="loioa3dfcb0284f21015b74ac3cded42ee69__grant_system_priv_remarks1"/>

## Remarks

By default, if no administrative clause is specified in the grant statement, the WITH NO ADMIN OPTION clause is used.



<a name="loioa3dfcb0284f21015b74ac3cded42ee69__grant_system_privileges1"/>

## Privileges



### 

You must have been granted the specific system privilege with administrative privilege.



<a name="loioa3dfcb0284f21015b74ac3cded42ee69__grant_system_priv_standards1"/>

## Standards

-   SQL – other syntaxes are vendor extensions to ISO/ANSI SQL grammar



## Examples

This example grants the CHECKPOINT system privilege to Sally with no administrative privileges:

```
GRANT CHECKPOINT TO Sally WITH NO ADMIN OPTION;
```

This example grants the MONITOR system privilege to Jane with administrative privileges only:

```
GRANT MONITOR TO Jane WITH ADMIN ONLY OPTION;
```

**Related Information**  


[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

