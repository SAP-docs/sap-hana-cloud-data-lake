<!-- loioa6139f4584f21015bdc3a625b5b218b5 -->

# ALTER USER Statement for Data Lake Relational Engine

Changes user settings.



<a name="loioa6139f4584f21015bdc3a625b5b218b5__section_xv3_wvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.





### Syntax 1 – Changes the Definition of a Database User

```
ALTER USER <user-name> 
   { [ IDENTIFIED BY <password> ]
   | [ LOGIN POLICY <policy-name> ]  
   | [ FORCE PASSWORD CHANGE { ON | OFF } ] };
```



### Syntax 2 – Refreshes the Distinguished Name \(DN\) for an LDAP User

```
ALTER USER <user-name> REFRESH DN;
```



### Syntax 2 – Reverts a User's Login Policy to the Original Values

```
ALTER USER <user-name> RESET LOGIN POLICY;
```



### Syntax 3 – Changes a User's Password when the CHANGE\_PASSOWRD\_DUAL\_CONTROL option is enabled

```
ALTER USER IDENTIFIED [ FIRST | LAST ] BY <password_part>;
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa6139f4584f21015bdc3a625b5b218b5__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

*<user-name\>*

</b></dt>
<dd>

A data lake Relational Engine user ID cannot:

-   begin with white space, single quotes, or double quotes
-   end with white space
-   contain semicolons



</dd><dt><b>

IDENTIFIED BY *<password\>*

</b></dt>
<dd>

Password of the user. You do not have to specify a password for the user. A user without a password cannot connect to the database. This is useful if you are creating a role and do not want anyone to connect to the database using the role user ID.

A data lake Relational Engine password must be minimum of 6 characters in length. For single-byte character sets, this value is the same as the number of characters. It must contain:

-   at least one number character \(0-9\)
-   at least one upper case Latin letter character \(A-Z\)
-   at least one lower case Latin letter character \(a-z\)

Passwords are case-sensitive and they cannot:

-   begin with white space, single quotes, or double quotes
-   end with white space
-   contain semicolons
-   be longer than 255 bytes in length
-   be less than 6 characters in length
-   contain the user’s ID \(user name\)
-   be the re-use of an old password for that user

The encryption algorithm used for hashing the user passwords is FIPS-certified encryption support:

-   The DLL is called dbfips17.dll.
-   The HASH function accepts the algorithms: SHA1\_FIPS SHA256\_FIPS.
-   If the -fips server option is specified and an algorithm that is not FIPS-certified is given to the HASH function, then the database server uses SHA1\_FIPS instead of SHA1, SHA256\_FIPS instead of SHA256, and returns an error if MD5 is used \(MD5 is not a FIPS-certified algorithm\).
-   If the -fips option is specified, then the database server uses SHA256\_FIPS for password hashing.



</dd><dt><b>

LOGIN POLICY *<policy-name\>*

</b></dt>
<dd>

Name of the login policy to assign the user. No change is made if you do not specify a login policy.



</dd><dt><b>

FORCE PASSWORD CHANGE

</b></dt>
<dd>

Controls whether the user must specify a new password upon logging in. This setting overrides the PASSWORD\_EXPIRY\_ON\_NEXT\_LOGIN option setting in the user's login policy.



</dd><dt><b>

REFRESH DN

</b></dt>
<dd>

Clause is not supportedClears the saved DN and timestamp for a user, which is used during LDAP authentication.



</dd><dt><b>

RESET LOGIN POLICY

</b></dt>
<dd>

Reverts the settings of the user's login to the original values in the login policy. This usually clears all locks that are implicitly set due to the user exceeding the failed logins or exceeding the maximum number of days since the last login. When you reset a login policy, a user can access an account that has been locked for exceeding a login policy option limit such as MAX\_FAILED\_LOGIN\_ATTEMPTS or MAX\_DAYS\_SINCE\_LOGIN.



</dd><dt><b>

IDENTIFIED \[ FIRST | LAST \] BY

</b></dt>
<dd>

Required when CHANGE\_PASSWORD\_DUAL\_CONTROL option is enabled in a target user's login policy. The FIRST and LAST keywords specify the part of the dual password part ing defined.



</dd>
</dl>



<a name="loioa6139f4584f21015bdc3a625b5b218b5__IQ_Usage"/>

## Remarks

If you set the PASSWORD\_EXPIRY\_ON\_NEXT\_LOGIN value to ON in the login policy, the passwords of all users assigned to this login policy expire immediately upon the next login. You can use the ALTER USER and LOGIN POLICY clauses to force users to change their passwords at the next login.

If the CHANGE\_PASSWORD\_DUAL CONTROL login policy option is disable \(OFF\) during the dual password change process:

-   The target user isbe unable to log in with the single password part already defined. The ALTER USER statement must be reissued using single password control syntax.
-   If the option is disabled after the dual password change process is complete, but before the target user logs in, there is no impact on the target user. The target user must log in using both password parts.

If the target user is already logged in when the dual password change process occurs, the user cannot change their password in the current session until both parts of the new password are set. Once the dual password change process is complete, the target user can use GRANT CONNECT or ALTER USER to change the password without first logging out. The prompt to enter the current password, use the new dual control password, not the password originally entered for the current session.

The GRANT CONNECT statement is not supported during for the dual password change process to set either password part. However, once the dual password change process is complete, the target user can use the GRANT CONNECT statement or ALTER USER to change their password without first logging out.

As soon as both parts of the password are successfully specified by users with the CHANGE PASSWORD system privilege, the password for the target user is automatically expired. This forces the target user to change the password the next time they log in.

Passwords are stored using secure one-way hashing with numerous security features. See [Understanding Security in Data Lake Relational Engine](https://help.sap.com/docs/SAP_HANA_DATA_LAKE/a89a0a8384f21015b1e7adbeca456f73/39783d0778ba47b7bbc2583b33af0f49.html).



<a name="loioa6139f4584f21015bdc3a625b5b218b5__alter_user_privileges1"/>

## Privileges

-   To change your own password, no additional privilege is required.
-   To change the password of another user requires the CHANGE PASSWORD system privilege.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



<a name="loioa6139f4584f21015bdc3a625b5b218b5__IQ_Standards"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loioa6139f4584f21015bdc3a625b5b218b5__IQ_Examples"/>

## Examples

The following example alters a user named SQLTester. The password is set to welcome. The SQLTester user is assigned to the Test1 login policy and the password does not expire on the next login:

```
ALTER USER SQLTester IDENTIFIED BY welcome
LOGIN POLICY Test1 FORCE PASSWORD CHANGE OFF;
```

The following example clears the distinguished name \(DN\) and timestamp for a user named Mary used for LDAP authentication:

```
ALTER USER Mary REFRESH DN;
```

The following example sets the password for user3 to PassPart1PassPart2. This assumes that user1 and user2 have the CHANGE PASSWORD system privilege and the change\_password\_dual\_control option is enabled \(ON\) in the login policy for user3:

1.  User1 enters:

    ```
    ALTER USER user3 IDENTIFIED FIRST BY PassPart1;
    ```

2.  User2 enters:

    ```
    ALTER USER user3 IDENTIFIED LAST BY PassPart2;
    ```

3.  Once set, User3 logs on by entering the password PassPart1PassPart2.

**Related Information**  


[COMMENT Statement for Data Lake Relational Engine](comment-statement-for-data-lake-relational-engine-a615ad2.md "Stores a comment, in the system tables, about a database object.")

[CREATE USER Statement for Data Lake Relational Engine](create-user-statement-for-data-lake-relational-engine-a619a5f.md "Creates a user.")

[DROP USER Statement for Data Lake Relational Engine](drop-user-statement-for-data-lake-relational-engine-a61d9fe.md "Removes a user.")

[GRANT ROLE Statement for Data Lake Relational Engine](grant-role-statement-for-data-lake-relational-engine-a3e379c.md "Grants roles to users or other roles, with or without administrative rights.")

[REVOKE ROLE Statement for Data Lake Relational Engine](revoke-role-statement-for-data-lake-relational-engine-a3e9de3.md "Removes a users membership in a role or his or her ability to administer the role.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[Login Policy Options](https://help.sap.com/viewer/745778e524f74bb4af87460cca5e62c4/2023_4_QRC/en-US/a43f448484f21015924f9951e9b77e32.html "Available options for CUSTOMER_ROOT and user-defined login policies.") :arrow_upper_right:

[ALTER USER Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/a9da89453d43402981a6e01fa8c7742d.html "Changes user settings.") :arrow_upper_right:

