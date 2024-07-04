<!-- loioa3e04cc984f2101598aba78be9f2b17d -->

# GRANT CONNECT Statement for Data Lake Relational Engine

Create a new user, and can also be used to change a password. However, it is recommended that you use the CREATE USER statement to create users instead of the GRANT CONNECT statement.



<a name="loioa3e04cc984f2101598aba78be9f2b17d__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
GRANT CONNECT TO <grantee> IDENTIFIED BY <password>
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa3e04cc984f2101598aba78be9f2b17d__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

*<grantee\>*

</b></dt>
<dd>

Must be the name of an existing user or role that has a login password.



</dd>
</dl>



<a name="loioa3e04cc984f2101598aba78be9f2b17d__IQ_Usage"/>

## Remarks

GRANT CONNECT can be used to create a new user or be used by any user to change their own password.

> ### Tip:  
> Use the CREATE USER statement rather than the GRANT CONNECT statement to create users.
> 
> If you inadvertently enter the user ID of an existing user when you are trying to add a new user, you are actually changing the password of the existing user. You do not receive a warning because this behavior is considered normal.

> ### Note:  
> Use system procedures, not GRANT and REVOKE statements to add and remove user IDs.

A user without a password cannot connect to the database. This is useful when you are creating groups and you do not want anyone to connect to the role user ID. To create a user without a password, do not include the IDENTIFIED BY clause.

When specifying a password, it must be a valid identifier. Passwords have a maximum length of 255 bytes. The GRANT CONNECT TO statement calls the function identified by the option value. The function returns NULL to indicate that the password conforms to rules.

Invalid names for database user IDs and passwords include those that:

-   Begin with white space or single or double quotes
-   End with white space
-   Contain semicolons



<a name="loioa3e04cc984f2101598aba78be9f2b17d__IQ_Permissions"/>

## Privileges

-   To change your own password requires no additional privilege.
-   To change another user's password requires the CHANGE PASSWORD system privilege.
-   To create a new user requires the MANAGE ANY USER system privilege.



<a name="loioa3e04cc984f2101598aba78be9f2b17d__IQ_Standards"/>

## Standards

-   SQL – other syntaxes are vendor extensions to ISO/ANSI SQL grammar
-   SAP database products – the security model is different in SAP Adaptive Server Enterprise and data lake Relational Engine, so other syntaxes differ.



<a name="loioa3e04cc984f2101598aba78be9f2b17d__IQ_Examples"/>

## Examples

The following example creates user `Jane` with no password:

```
GRANT CONNECT TO Jane;
```

The following example changes the password for `Bob` to `newpassword`:

```
GRANT CONNECT TO Bob IDENTIFIED BY <newpassword>;
```

**Related Information**  


[CREATE USER Statement for Data Lake Relational Engine](create-user-statement-for-data-lake-relational-engine-a619a5f.md "Creates a user.")

[REVOKE CONNECT Statement for Data Lake Relational Engine](revoke-connect-statement-for-data-lake-relational-engine-a3e6a6f.md "Removes a user from the database.")

