<!-- loioa9da89453d43402981a6e01fa8c7742d -->

# ALTER USER Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Changes user settings.



<a name="loioa9da89453d43402981a6e01fa8c7742d__section_kyf_nhw_ysb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:

-   Connected directly to data lake Relational Engine **coordinator** as a data lake Relational Engine user. This syntax cannot be run using the REMOTE\_EXECUTE procedure.





```
ALTER USER <user-name> 
   { [ IDENTIFIED BY <password> ]
   | [ LOGIN POLICY <policy-name> ]  
   | [ FORCE PASSWORD CHANGE { ON | OFF } ] }
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa9da89453d43402981a6e01fa8c7742d__section_x5s_trq_wwb"/>

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



<a name="loioa9da89453d43402981a6e01fa8c7742d__section_mxr_5rq_wwb"/>

## Remarks

If you set the PASSWORD\_EXPIRY\_ON\_NEXT\_LOGIN value to ON in the login policy, the passwords of all users assigned to this login policy expire immediately upon the next login. You can use the ALTER USER and LOGIN POLICY clauses to force users to change their passwords at the next login.

Passwords are stored using secure one-way hashing with numerous security features. See [Understanding Security in Data Lake Relational Engine](https://help.sap.com/docs/SAP_HANA_DATA_LAKE/a89a0a8384f21015b1e7adbeca456f73/39783d0778ba47b7bbc2583b33af0f49.html).



<a name="loioa9da89453d43402981a6e01fa8c7742d__section_mbm_jsq_wwb"/>

## Privileges

-   To change your own password, no additional privilege is required.
-   To change the password of another user requires the CHANGE PASSWORD system privilege.



<a name="loioa9da89453d43402981a6e01fa8c7742d__section_fcb_1sq_wwb"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loioa9da89453d43402981a6e01fa8c7742d__section_c1n_bsq_wwb"/>

## Examples

**Related Information**  


[CREATE USER Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](create-user-statement-for-data-lake-relational-engine-sap-hana-db-managed-a21f652.md "Creates a user.")

[DROP USER Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](drop-user-statement-for-data-lake-relational-engine-sap-hana-db-managed-d94380c.md "Removes a user.")

[ALTER USER Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a6139f4584f21015bdc3a625b5b218b5.html "Changes user settings.") :arrow_upper_right:

[User ID and Password Restrictions and Considerations](https://help.sap.com/viewer/a89a0a8384f21015b1e7adbeca456f73/2024_3_QRC/en-US/a46126b284f21015bae2a1c9bb31c205.html "A user must have a user ID and password to connect to the database.") :arrow_upper_right:

