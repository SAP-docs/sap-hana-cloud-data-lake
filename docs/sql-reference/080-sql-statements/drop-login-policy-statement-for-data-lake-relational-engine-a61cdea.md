<!-- loioa61cdea584f21015ac4bf1af4e15280c -->

# DROP LOGIN POLICY Statement for Data Lake Relational Engine

Removes a login policy from the database.



<a name="loioa61cdea584f21015ac4bf1af4e15280c__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
DROP LOGIN POLICY <policy-name>;
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa61cdea584f21015ac4bf1af4e15280c__IQ_Usage"/>

## Remarks

A `DROP LOGIN POLICY` statement fails if you attempt to drop a policy that is assigned to a user. You can use either the `ALTER USER` statement to change the policy assignment of the user or `DROP USER` to drop the user.



<a name="loioa61cdea584f21015ac4bf1af4e15280c__IQ_Permissions"/>

## Privileges

Requires the MANAGE ANY LOGIN POLICY system privilege.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



<a name="loioa61cdea584f21015ac4bf1af4e15280c__IQ_Examples"/>

## Examples

The following example creates, then deletes, the `Test11` login policy:

```
CREATE LOGIN POLICY Test11; 
DROP LOGIN POLICY Test11 ;
```

**Related Information**  


[CREATE LOGIN POLICY Statement for Data Lake Relational Engine](create-login-policy-statement-for-data-lake-relational-engine-a617f94.md "Creates a login policy in the database.")

[ALTER LOGIN POLICY Statement for Data Lake Relational Engine](alter-login-policy-statement-for-data-lake-relational-engine-a231c98.md "Changes existing login policies .")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

