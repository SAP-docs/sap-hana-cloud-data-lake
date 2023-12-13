<!-- loioa617f94484f210158939e870e250dd78 -->

# CREATE LOGIN POLICY Statement for Data Lake Relational Engine

Creates a login policy in the database.



<a name="loioa617f94484f210158939e870e250dd78__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
CREATE LOGIN POLICY <policy-name> <policy-option>;
```

```
<policy-option> ::=
   [<policy-option-name> = <policy-option-value>...];
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
   { UNLIMITED | DEFAULT | NULL | <value> };
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa617f94484f210158939e870e250dd78__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

*<policy-name\>*

</b></dt>
<dd>

The name of the login policy.



</dd>
</dl>


<dl>
<dt><b>

*<policy-option-name\>*

</b></dt>
<dd>

The name of the policy option. See [Login Policy Options](https://help.sap.com/viewer/745778e524f74bb4af87460cca5e62c4/2023_4_QRC/en-US/a43f448484f21015924f9951e9b77e32.html "Available options for CUSTOMER_ROOT and user-defined login policies.") :arrow_upper_right: for details about each option.



</dd><dt><b>

*<policy-option-value\>*

</b></dt>
<dd>

The value assigned to the login policy option. If you specify UNLIMITED, then no limits are used. If you specify DEFAULT, then the default limits are used. See [Login Policy Options](https://help.sap.com/viewer/745778e524f74bb4af87460cca5e62c4/2023_4_QRC/en-US/a43f448484f21015924f9951e9b77e32.html "Available options for CUSTOMER_ROOT and user-defined login policies.") :arrow_upper_right: for supported values for each option.

NULL and UNLIMITED are not valid for some options.



</dd>
</dl>



<a name="loioa617f94484f210158939e870e250dd78__IQ_Usage"/>

## Remarks

If you do not specify a policy option, then values for this login policy come from the CUSTOMER\_root login policy. New policies do not inherit the MAX\_NON\_DBA\_CONNECTIONS and ROOT\_AUTO\_UNLOCK\_TIME policy options.

All new instances include a CUSTOMER\_root login policy, which cannot be modified or deleted.

For details on available login policy options for CUSTOMER\_root and user-defined logins and LDAP user authentication, see:

-   [Login Policy Options](https://help.sap.com/viewer/745778e524f74bb4af87460cca5e62c4/2023_4_QRC/en-US/a43f448484f21015924f9951e9b77e32.html "Available options for CUSTOMER_ROOT and user-defined login policies.") :arrow_upper_right:
-   [LDAP Login Policy Options](https://help.sap.com/viewer/745778e524f74bb4af87460cca5e62c4/2023_4_QRC/en-US/a450848584f210159c6ab461ae64c77f.html "Available login policy options for LDAP user authentication.") :arrow_upper_right:



<a name="loioa617f94484f210158939e870e250dd78__IQ_Permissions"/>

## Privileges

Requires the MANAGE ANY LOGIN POLICY system privilege.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.

The MANAGE ANY USER system privilege can override the LOCKED and MAX\_DAYS\_SINCE\_LOGIN options.



<a name="loioa617f94484f210158939e870e250dd78__IQ_Examples"/>

## Examples

The following example creates the `Test3` login policy, which uses the JWT login mode for user authentication.

```
CREATE LOGIN POLICY Test3
LOGIN_MODE="JWT";
```

**Related Information**  


[ALTER LOGIN POLICY Statement for Data Lake Relational Engine](alter-login-policy-statement-for-data-lake-relational-engine-a231c98.md "Changes existing login policies .")

[DROP LOGIN POLICY Statement for Data Lake Relational Engine](drop-login-policy-statement-for-data-lake-relational-engine-a61cdea.md "Removes a login policy from the database.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

