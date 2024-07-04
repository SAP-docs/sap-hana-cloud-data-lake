<!-- loioa21f6524ecab45fcaa89b6f9bf4670e8 -->

# CREATE USER Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Creates a user.



<a name="loioa21f6524ecab45fcaa89b6f9bf4670e8__section_pkx_2ns_nyb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:

-   Connected directly to data lake Relational Engine **coordinator** as a data lake Relational Engine user. This syntax cannot be run using the REMOTE\_EXECUTE procedure.



```
CREATE USER <user-name>  [ IDENTIFIED BY <password> ]
   [ LOGIN POLICY <policy-name> ]
   [ FORCE PASSWORD CHANGE { ON | OFF } ]
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa21f6524ecab45fcaa89b6f9bf4670e8__section_qdf_djg_xvb"/>

## Parameters


<dl>
<dt><b>

*<user-name\>*

</b></dt>
<dd>

A data lake Relational Engine user ID can't:

-   begin with white space, single quotes, or double quotes
-   end with white space
-   contain semicolons



</dd><dt><b>

IDENTIFIED BY *<password\>*

</b></dt>
<dd>

Password of the user. You do not have to specify a password for the user. A user without a password cannot connect to the database. This is useful if you are creating a role and do not want anyone to connect to the database using the role user ID.

A data lake Relational Engine password must be a minimum of 6 characters in length. For single-byte character sets, this value is the same as the number of characters. It must contain:

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



</dd>
</dl>



<a name="loioa21f6524ecab45fcaa89b6f9bf4670e8__section_t51_lns_nyb"/>

## Privileges

Requires the MANAGE ANY USER system privilege.



<a name="loioa21f6524ecab45fcaa89b6f9bf4670e8__section_ok5_hjg_xvb"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loioa21f6524ecab45fcaa89b6f9bf4670e8__section_l2g_3jg_xvb"/>

## Examples

The following example creates a user named SQLTester with the password welcome. The SQLTester user is assigned to the Test1 login policy and the password expires on the next login:

```
CREATE USER SQLTester IDENTIFIED BY welcome
LOGIN POLICY Test1 FORCE PASSWORD CHANGE ON;
```

**Related Information**  


[ALTER USER Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](alter-user-statement-for-data-lake-relational-engine-sap-hana-db-managed-a9da894.md "Changes user settings.")

[DROP USER Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](drop-user-statement-for-data-lake-relational-engine-sap-hana-db-managed-d94380c.md "Removes a user.")

[CREATE USER Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a619a5f184f210158155ea1a4fe03da8.html "Creates a user.") :arrow_upper_right:

[User ID and Password Restrictions and Considerations](https://help.sap.com/viewer/a89a0a8384f21015b1e7adbeca456f73/2024_3_QRC/en-US/a46126b284f21015bae2a1c9bb31c205.html "A user must have a user ID and password to connect to the database.") :arrow_upper_right:

