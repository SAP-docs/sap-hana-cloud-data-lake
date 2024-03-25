<!-- loioa231c98584f21015b4c9a28d37a9c8d1 -->

# ALTER LOGIN POLICY Statement for Data Lake Relational Engine

Changes existing login policies .



<a name="loioa231c98584f21015b4c9a28d37a9c8d1__section_azh_5fj_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
ALTER LOGIN POLICY <policy-name> <policy-option>
```

```
<policy-option> ::=
   <policy-option-name> = <policy-option-value>
```

```
<policy-option-name> ::=
   { AUTO_UNLOCK_TIME 
   | CHANGE_PASSWORD_DUAL_CONTROL
   | LOCKED 
   | LOGIN_MODE 
   | MAX_CONNECTIONS 
   | MAX_DAYS_SINCE_LOGIN 
   | MAX_FAILED_LOGIN_ATTEMPTS 
   | MAX_NON_DBA_CONNECTIONS
   | PASSWORD_EXPIRY_ON_NEXT_LOGIN 
   | PASSWORD_GRACE_TIME 
   | PASSWORD_LIFE_TIME 
   | ROOT_AUTO_UNLOCK_TIME }
```

```
<policy-option-value> ::=
   { UNLIMITED | DEFAULT | NULL | <value> }
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa231c98584f21015b4c9a28d37a9c8d1__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

*<policy-name\>*

</b></dt>
<dd>

The name of the login policy. You cannot alter the CUSTOMER\_ROOT login policy.



</dd>
</dl>


<dl>
<dt><b>

*<policy-option-name\>*

</b></dt>
<dd>

The name of the policy option. See [Login Policy Options](https://help.sap.com/viewer/a89a0a8384f21015b1e7adbeca456f73/2024_1_QRC/en-US/a43f448484f21015924f9951e9b77e32.html "Available options for CUSTOMER_ROOT and user-defined login policies.") :arrow_upper_right: for details about each option.



</dd><dt><b>

*<policy-option-value\>*

</b></dt>
<dd>

The value assigned to the login policy option. If you specify UNLIMITED, then no limits are used. If you specify DEFAULT, then the default limits are used. See [Login Policy Options](https://help.sap.com/viewer/a89a0a8384f21015b1e7adbeca456f73/2024_1_QRC/en-US/a43f448484f21015924f9951e9b77e32.html "Available options for CUSTOMER_ROOT and user-defined login policies.") :arrow_upper_right: for supported values for each option.

NULL and UNLIMITED are not valid for some options.



</dd>
</dl>



<a name="loioa231c98584f21015b4c9a28d37a9c8d1__IQ_Usage"/>

## Remarks

If you do not specify a policy option, then values for this login policy come from the CUSTOMER\_root login policy. New policies do not inherit the MAX\_NON\_DBA\_CONNECTIONS and ROOT\_AUTO\_UNLOCK\_TIME policy options.

All new instances include a CUSTOMER\_root login policy, which cannot be modified or deleted.

For details on available login policy options for CUSTOMER\_root and user-defined logins and LDAP user authentication, see:

-   [Login Policy Options](https://help.sap.com/viewer/a89a0a8384f21015b1e7adbeca456f73/2024_1_QRC/en-US/a43f448484f21015924f9951e9b77e32.html "Available options for CUSTOMER_ROOT and user-defined login policies.") :arrow_upper_right:
-   [LDAP Login Policy Options](https://help.sap.com/viewer/a89a0a8384f21015b1e7adbeca456f73/2024_1_QRC/en-US/a450848584f210159c6ab461ae64c77f.html "Available login policy options for LDAP user authentication.") :arrow_upper_right:



<a name="loioa231c98584f21015b4c9a28d37a9c8d1__IQ_Permissions"/>

## Privileges

Requires the MANAGE ANY LOGIN POLICY system privilege.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



<a name="loioa231c98584f21015b4c9a28d37a9c8d1__IQ_Examples"/>

## Examples

This example sets the LOGIN\_MODE to both standard, and JWT authentication mode.

```
ALTER LOGIN POLICY Test1
LOGIN_MODE="Standard,JWT";
```

The following example sets the LOGIN\_MODE to NULL. This defaults to the CUSTOMER\_root policy.

```
ALTER LOGIN POLICY Test2
LOGIN_MODE="NULL";
```

The following example sets the password\_life\_time value to `180` and the max\_failed\_login\_attempts value to `5` in the `Test2` login policy:

```
ALTER LOGIN POLICY Test3 
password_life_time=180
max_failed_login_attempts=5;
```

**Related Information**  


[CREATE LOGIN POLICY Statement for Data Lake Relational Engine](create-login-policy-statement-for-data-lake-relational-engine-a617f94.md "Creates a login policy in the database.")

[DROP LOGIN POLICY Statement for Data Lake Relational Engine](drop-login-policy-statement-for-data-lake-relational-engine-a61cdea.md "Removes a login policy from the database.")

[Login Policy Options](https://help.sap.com/viewer/a89a0a8384f21015b1e7adbeca456f73/2024_1_QRC/en-US/a43f448484f21015924f9951e9b77e32.html "Available options for CUSTOMER_ROOT and user-defined login policies.") :arrow_upper_right:

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

