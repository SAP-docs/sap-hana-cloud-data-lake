<!-- loioa426f91384f21015b827d45ce9fce3a7 -->

# VALIDATE LDAP SERVER Statement for Data Lake Relational Engine

Validates changes to the settings of existing LDAP server configuration objects before applying them.



<a name="loioa426f91384f21015b827d45ce9fce3a7__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
VALIDATE LDAP SERVER [ { <ldapua-server-name> | <ldapua-server-attributes> } ]
   [ CHECK <userid> [ <user-dn-string> ] ];
```

```
<ldapua-server-attributes> ::=
   { SEARCH DN
      { URL { '<URL_string>' | NULL } 
         | ACCESS ACCOUNT { '<DN_string>' | NULL } 
         | IDENTIFIED BY { '<password>' | NULL }
      | AUTHENTICATION URL { '<URL_string>' | NULL } 
      | CONNECTION TIMEOUT <timeout_value> 
      | CONNECTION RETRIES <retry_value>  };
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa426f91384f21015b827d45ce9fce3a7__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

*<ldapua-server-name\>*

</b></dt>
<dd>

Identifies the LDAP server configuration object.



</dd><dt><b>

URL \{ '*<URL\_string\>*' | NULL \}

</b></dt>
<dd>

Identifies the host \(by name or by IP address\), port number, and the search to be performed for the DN lookup for a given user ID. This value is validated for correct LDAP URL syntax before it is stored in the `ISYSLDAPSERVER` system table. The maximum size for this string is 1024 bytes.



</dd><dt><b>

ACCESS ACCOUNT \{ '*<DN\_string\>*' | NULL \}

</b></dt>
<dd>

A user created on the LDAP server for use by data lake Relational Engine, not a user within data lake Relational Engine. The distinguished name \(DN\) for this user is used to connect to the LDAP server. This user has permissions within the LDAP server to search for DNs by user ID in the locations specified by the SEARCH DN URL. The maximum size for this string is 1024 bytes.



</dd><dt><b>

IDENTIFIED BY \{ '*<password\>*' | NULL \}

</b></dt>
<dd>

Provides the password associated with the ACCESS ACCOUNT user. The password is stored using symmetric encryption on disk. Use the value NULL to clear the password and set it to none. The maximum size of a clear text password is 255 bytes.



</dd><dt><b>

IDENTIFIED BY ENCRYPTED \{ *<encrypted-password\>* | NULL \}

</b></dt>
<dd>

Configures the password associated with the ACCESS ACCOUNT distinguished name in an encrypted format. The binary value is the encrypted password and is stored on disk as is. Use the value NULL to clear the password and set it to none. The maximum size of the binary is 289 bytes.



</dd><dt><b>

AUTHENTICATION URL \{ '*<URL\_string\>*' | NULL \}

</b></dt>
<dd>

Identifies the host \(by name or IP address\) and the port number of the LDAP server to use for authentication of the user. This is the value defined for *<URL\_string\>* and is validated for correct LDAP URL syntax before it is stored in `ISYSLDAPSERVER` system table. The DN of the user obtained from a prior DN search and the user password bind a new connection to the authentication URL. A successful connection to the LDAP server is considered proof of the identity of the connecting user. The maximum size for this string is 1024 bytes.



</dd><dt><b>

CONNECTION TIMEOUT *<timeout\_value\>*

</b></dt>
<dd>

Specifies the connection timeout from data lake Relational Engine to the LDAP server for both DN searches and authentication. This value is in milliseconds, with a default value of 10 seconds.



</dd><dt><b>

CONNECTION RETRIES*<retry\_value\>*

</b></dt>
<dd>

Specifies the number of retries on connections from data lake Relational Engine to the LDAP server for both DN searches and authentication. The valid range of values is 1 through 60, with a default value of 3.



</dd><dt><b>

CHECK *<userid\>*

</b></dt>
<dd>

The userID whose existence is validated on the LDAP server.



</dd><dt><b>

*<user-dn-string\>*

</b></dt>
<dd>

Compares a user's DN value with the user ID for verification purposes.



</dd>
</dl>



<a name="loioa426f91384f21015b827d45ce9fce3a7__IQ_Usage"/>

## Remarks

`VALIDATE LDAP SERVER` statement is temporary and is closed by the end of the statement.This statement is useful for an administrator when setting up a new server to use LDAP user authentication, and for diagnosing problems between the LDAP server configuration object and the external LDAP server. Any connection made by the

When validating the LDAP server configuration object by name, definitions from prior `CREATE LDAP SERVER` and `ALTER LDAP SERVER` statements are used. Alternately, when *<ldapua-server-attributes\>* are specified instead of the LDAP server configuration object name, the specified attributes are validated. When *<ldapua-server-attributes\>* are specified, the URLs are parsed to identify syntax errors, and statement processing stops is a syntax error is detected.

Whether using an LDAP server configuration object name or a successfully parsed set of *<ldapua-server-attributes\>*, a connection to the external LDAP server is attempted. If the parameter ACCESS ACCOUNT and a password are specified, the values are used to establish the connection to the SEARCH DN URL. This is the SEARCH DN URL, ACCESS ACCOUNT, and ACCESS ACCOUNT password.

When using the optional CHECK clause, the userID is used in the search to validate the existence of the user on the external LDAP server.  When the expected DN value for a given user is known, the value can be specified, and is compared with the result of the search to determine success or failure.



<a name="loioa426f91384f21015b827d45ce9fce3a7__IQ_Permissions"/>

## Privileges

Requires the MANAGE ANY LDAP SERVER system privilege.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



<a name="loioa426f91384f21015b827d45ce9fce3a7__IQ_Standards"/>

## Standards

ANSI SQL – compliance level: Transact-SQL extension



<a name="loioa426f91384f21015b827d45ce9fce3a7__IQ_Examples"/>

## Examples

-   This example assumes the apps\_primary LDAP server configuration object was created as follows:

    ```
    CREATE LOGIN POLICY ldaptest LOGIN_MODE="Standard,LDAPUA";
    CREATE LDAP SERVER apps_primary 
    SEARCH DN 
    	URL 'ldaps://my_LDAPserver:389/dc=MyCompany,dc=com??sub?cn=*' 
    	ACCESS ACCOUNT 'cn=aseadmin, cn=Users, dc=mycompany, dc=com' 
    	IDENTIFIED BY 'Secret99Password' 
    AUTHENTICATION URL 'ldaps://my_LDAPserver:389/' 
    CONNECTION TIMEOUT 3000 
    WITH ACTIVATE;
    ```

-   This example validates the existence of a userID `myusername`This statement is useful for an administrator when setting up a new server by using the optional CHECK clause to compare the userID to the expected user distinguished name \(enclosed in quotation marks\) on the `apps_primary` LDAP server configuration object:

    ```
    VALIDATE LDAP SERVER apps_primary
    CHECK myusername 'cn=myusername,cn=Users,dc=mycompany,dc=com';
     
    ```

-   In this example, the name of the LDAP server configuration object does not have to defined in the `VALIDATE LDAP SERVER` statement if you include the search attributes:

    ```
    VALIDATE LDAP SERVER 
    SEARCH DN 
    	URL  'ldaps://my_LDAPserver:389/dc=MyCompany,dc=com??sub?cn=*' 
    	ACCESS ACCOUNT 'cn=aseadmin, cn=Users, dc=mycompany, dc=com'
    	IDENTIFIED BY 'Secret99Password'
    AUTHENTICATION URL 'ldaps://my_LDAPserver:389/'
    CONNECTION TIMEOUT 3000
    CHECK myusername 'cn=myusername,cn=Users,dc=mycompany,dc=com';
     
    ```


**Related Information**  


[DROP LDAP SERVER Statement for Data Lake Relational Engine](drop-ldap-server-statement-for-data-lake-relational-engine-a426759.md "Removes the named LDAP server configuration object from the SYSLDAPSERVER system view after verifying that the LDAP server configuration object is not in a READY or ACTIVE state.")

[CREATE LDAP SERVER Statement for Data Lake Relational Engine](create-ldap-server-statement-for-data-lake-relational-engine-a424e90.md "Creates a new LDAP server configuration object for LDAP user authentication. Parameters defined during the creation of an LDAP server configuration object are stored in the ISYSLDAPSERVER (system view SYSLDAPSERVER) system table.")

[ALTER LDAP SERVER Statement for Data Lake Relational Engine](alter-ldap-server-statement-for-data-lake-relational-engine-a425eb5.md "Any changes to an LDAP server configuration object are applied on subsequent connections. Any connection already started when the change is applied does not immediately reflect the change.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

