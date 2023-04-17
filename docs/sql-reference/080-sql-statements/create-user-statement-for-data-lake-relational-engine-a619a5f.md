<!-- loioa619a5f184f210158155ea1a4fe03da8 -->

# CREATE USER Statement for Data Lake Relational Engine

Creates a user.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
CREATE USER <user-name>  [ IDENTIFIED BY <password> ]
   [ LOGIN POLICY [/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <policy-name> (varname] ]
   [ FORCE PASSWORD CHANGE { ON | OFF } ]
```



<a name="loioa619a5f184f210158155ea1a4fe03da8__create_user_parameters1"/>

## Parameters

 *<user-name\>*
 :   A data lake Relational Engine user ID cannot:

    -   begin with white space, single quotes, or double quotes
    -   end with white space
    -   contain semicolons

  IDENTIFIED BY *<password\>*
 :   Password of the user. You do not have to specify a password for the user. A user without a password cannot connect to the database. This is useful if you are creating a role and do not want anyone to connect to the database using the role user ID.

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

  LOGIN POLICY *<policy-name\>*
 :   Name of the login policy to assign the user. No change is made if you do not specify a login policy.

  FORCE PASSWORD CHANGE
 :   Controls whether the user must specify a new password upon logging in. This setting overrides the PASSWORD\_EXPIRY\_ON\_NEXT\_LOGIN option setting in the user's login policy.

 

<a name="loioa619a5f184f210158155ea1a4fe03da8__IQ_Permissions"/>

## Privileges

Requires the MANAGE ANY USER system privilege.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



<a name="loioa619a5f184f210158155ea1a4fe03da8__create_user_standards1"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loioa619a5f184f210158155ea1a4fe03da8__create_user_examples1"/>

## Examples

The following example creates a user named SQLTester with the password welcome. The SQLTester user is assigned to the Test1 login policy and the password expires on the next login:

```
CREATE USER SQLTester IDENTIFIED BY welcome
LOGIN POLICY Test1 FORCE PASSWORD CHANGE ON;
```

**Related Information**  


[ALTER USER Statement for Data Lake Relational Engine](alter-user-statement-for-data-lake-relational-engine-a6139f4.md "Changes user settings.")

[DROP USER Statement for Data Lake Relational Engine](drop-user-statement-for-data-lake-relational-engine-a61d9fe.md "Removes a user.")

[COMMENT Statement for Data Lake Relational Engine](comment-statement-for-data-lake-relational-engine-a615ad2.md "Stores a comment, in the system tables, about a database object.")

[GRANT ROLE Statement for Data Lake Relational Engine](grant-role-statement-for-data-lake-relational-engine-a3e379c.md "Grants roles to users or other roles, with or without administrative rights.")

[VERIFY\_PASSWORD\_FUNCTION Option for Data Lake Relational Engine](../090-database-options/verify-password-function-option-for-data-lake-relational-engine-a6672af.md "Specifies a user-supplied authentication function that can be used to implement password rules.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[Login Policy Options](https://help.sap.com/viewer/745778e524f74bb4af87460cca5e62c4/2023_1_QRC/en-US/a43f448484f21015924f9951e9b77e32.html "Available options for CUSTOMER_ROOT and user-defined login policies.") :arrow_upper_right:

