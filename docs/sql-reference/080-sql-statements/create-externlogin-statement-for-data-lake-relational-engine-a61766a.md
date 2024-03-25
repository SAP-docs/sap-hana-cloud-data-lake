<!-- loioa61766ae84f210158170ef9548a5e449 -->

# CREATE EXTERNLOGIN Statement for Data Lake Relational Engine

Assigns an alternate login name and password to be used when communicating with a remote server.



<a name="loioa61766ae84f210158170ef9548a5e449__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
CREATE EXTERNLOGIN <login-name> 
   TO <remote-server> 
   REMOTE LOGIN <remote-user> 
   [ IDENTIFIED BY <remote-password> ]
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa61766ae84f210158170ef9548a5e449__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

*<login-name\>*

</b></dt>
<dd>

Specifies the local user login name. When using integrated logins, the *<login-name\>* is the database user to which the Windows user ID is mapped.



</dd><dt><b>

TO *<remote-server\>*

</b></dt>
<dd>

Specifies the name of the remote server.



</dd><dt><b>

REMOTE LOGIN *<remote-user\>*

</b></dt>
<dd>

Specifies the user account on *<remote-server\>* for the local user *<login-name\>*.



</dd><dt><b>

IDENTIFIED BY *<remote-password\>*

</b></dt>
<dd>

\(Optional\) Specifies that *<remote-password\>* is the password for *<remote-user\>*. If you omit the IDENTIFIED BY clause, the password is sent to the remote server as NULL. If you specify IDENTIFIED BY " " \(an empty string\), the password sent is the empty string.



</dd>
</dl>



<a name="loioa61766ae84f210158170ef9548a5e449__IQ_Usage"/>

## Remarks

Changes made by `CREATE EXTERNLOGIN` do not take effect until the next connection to the remote server.

By default, data lake Relational Engine uses the names and passwords of its clients whenever it connects to a remote server on behalf of those clients. `CREATE EXTERNLOGIN` assigns an alternate login name and password to be used when communicating with a remote server. It stores the password internally in encrypted form.

The *<remote\_server\>* must be known to the local server by an entry in the `ISYSSERVER` system table. For more information, see the *CREATE SERVER Statement*.

Creating a remote login with the `CREATE EXTERNLOGIN` statement and defining a remote server with a `CREATE SERVER` statement sets up an external login and password for the INSERT...LOCATION such that any user can use the login and password in any context. This avoids possible errors due to inaccessibility of the login or password, and is the recommended way to connect to a remote server.

> ### Note:  
> If you rely on the user ID and password of the current connection, and a user changes the password, you must stop and restart the server before the new password takes effect on the remote server. Remote logins created with `CREATE EXTERNLOGIN` are unaffected by changes to the password for the default user ID.

Sites with automatic password expiration should plan for periodic updates of passwords for external logins.

`CREATE EXTERNLOGIN` cannot be used from within a transaction.

The *<remote-user\>* and *<remote-password\>* combination must be valid on *<remote-server\>*.



<a name="loioa61766ae84f210158170ef9548a5e449__IQ_Permissions"/>

## Privileges

Requires the MANAGE ANY USER system privilege.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



<a name="loioa61766ae84f210158170ef9548a5e449__IQ_Side_Effects"/>

## Side Effects

Automatic commit



<a name="loioa61766ae84f210158170ef9548a5e449__IQ_Standards"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products – supported by Open Client/Open Server



<a name="loioa61766ae84f210158170ef9548a5e449__IQ_Examples"/>

## Examples

The following example maps the local user named `DBA` to the user `sa` with password 4TKNOX when connecting to the server `mydb1`:

```
CREATE EXTERNLOGIN dba 
TO mydb1 
REMOTE LOGIN sa
IDENTIFIED BY 4TKNOX;
```

**Related Information**  


[CREATE SERVER Statement for Data Lake Relational Engine](create-server-statement-for-data-lake-relational-engine-a619187.md "Creates a remote server.")

[DROP EXTERNLOGIN Statement for Data Lake Relational Engine](drop-externlogin-statement-for-data-lake-relational-engine-a61caee.md "Drops an external login from the data lake Relational Engine system tables.")

[INSERT Statement for Data Lake Relational Engine](insert-statement-for-data-lake-relational-engine-a61fdef.md "Inserts a single row or a selection of rows, from elsewhere in the current database, into the table. This command can also insert a selection of rows from another database into the table.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

