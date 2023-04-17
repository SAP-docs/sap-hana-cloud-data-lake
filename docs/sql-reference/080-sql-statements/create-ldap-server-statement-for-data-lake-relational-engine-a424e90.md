<!-- loioa424e90384f21015bd3286d6da351964 -->

# CREATE LDAP SERVER Statement for Data Lake Relational Engine

Creates a new LDAP server configuration object for LDAP user authentication. Parameters defined during the creation of an LDAP server configuration object are stored in the `ISYSLDAPSERVER` \(system view `SYSLDAPSERVER`\) system table.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
CREATE LDAP SERVER <ldapua-server-name>
   [ { SEARCH DN
      { URL { '[/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <URL_string> (varname]' | NULL } 
         | ACCESS ACCOUNT { '[/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <DN_string> (varname]' | NULL } 
         | IDENTIFIED BY { '[/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <password> (varname]' | NULL }
      | AUTHENTICATION URL { '[/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <URL_string> (varname]' | NULL } 
      | CONNECTION TIMEOUT [/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <timeout_value> (varname] 
      | CONNECTION RETRIES [/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <retry_value> (varname] 
      | TLS OFF }  } ]
   [ WITH ACTIVATE ]
```



<a name="loioa424e90384f21015bd3286d6da351964__IQ_Parameters"/>

## Parameters

 URL '*<URL\_string\>*'
 :   Identifies the host \(by name or by IP address\), port number, and the search to be performed for the DN lookup for a given user ID. This value is validated for correct LDAP URL syntax before it is stored in the ISYSLDAPSERVER system table. The maximum size for this string is 1024 bytes.

  ACCESS ACCOUNT \{ '*<DN\_string\>*' | NULL \}
 :   User created in the LDAP server for use by data lake Relational Engine, not a user within data lake Relational Engine. The distinguished name \(DN\) for this user is used to connect to the LDAP server. This user has permissions within the LDAP server to search for DNs by user ID in the locations specified by the SEARCH DN URL. The maximum size for this string is 1024 bytes.

  IDENTIFIED BY \{ '*<password\>*' | NULL \}
 :   Provides the password associated with the ACCESS ACCOUNT user. The password is stored using symmetric encryption on disk. Use the value NULL to clear the password and set it to none. The maximum size of a clear text password is 255 bytes.

  AUTHENTICATION URL \{ '*<URL\_string\>*' | NULL \}
 :   Identifies the host \(by name or IP address\) and the port number of the LDAP server to use for authentication of the user. This is the value defined for URL\_string and is validated for correct LDAP URL syntax before it is stored in `ISYSLDAPSERVER` system table. The DN of the user obtained from a prior DN search and the user password bind a new connection to the authentication URL. A successful connection to the LDAP server is considered proof of the identity of the connecting user. The maximum size for this string is 1024 bytes.

  CONNECTION TIMEOUT *<timeout\_value\>*
 :   Identifies the host \(by name or IP address\) and the port number of the LDAP server to use for authentication of the user. This is the value defined for URL\_string and is validated for correct LDAP URL syntax before it is stored in `ISYSLDAPSERVER` system table. The DN of the user obtained from a prior DN search and the user password bind a new connection to the authentication URL. A successful connection to the LDAP server is considered proof of the identity of the connecting user. The maximum size for this string is 1024 bytes.

  CONNECTION RETRIES *<retry\_value\>*
 :   Specifies the number of retries on connections from data lake Relational Engine to the LDAP server for both DN searches and authentication. The valid range of values is 1– 60, with a default value of 3.

  TLS OFF
 :   Defines whether the TLS or Secure LDAP protocol is used for connections to the LDAP server for both DN searches and authentication. When set to OFF \(or not specified\), Secure LDAP protocol is used and the URL begins with “ldaps://”. When using the TLS protocol, specify the database security option TRUSTED\_CERTIFICATES\_FILE with a file name containing the certificate of the Certificate Authority \(CA\) that signed the certificate used by the LDAP server.

  WITH ACTIVATE
 :   Activates the LDAP server configuration object for immediate use upon creation. This permits the definition and activation of LDAP User Authentication in one statement. The LDAP server configuration object state changes to READY when WITH ACTIVATE is used.

 

<a name="loioa424e90384f21015bd3286d6da351964__IQ_Permissions"/>

## Privileges

Requires the MANAGE ANY LDAP SERVER system privilege.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



<a name="loioa424e90384f21015bd3286d6da351964__IQ_Standards"/>

## Standards

ANSI SQL – compliance level: Transact-SQL extension.



<a name="loioa424e90384f21015bd3286d6da351964__IQ_Examples"/>

## Examples

-   The following example sets the search parameters, the authentication URL, and sets a three second timeout, and activates the server so it can begin authenticating users. It connects to the LDAP server without TLS or SECURE LDAP protocols:

    ```
    SET OPTION PUBLIC.login_mode = 'Standard,LDAPUA' 
    CREATE LDAP SERVER apps_primary
    AUTHENTICATION URL 'ldaps://my_LDAPserver:389/' 
    CONNECTION TIMEOUT 3000 
    WITH ACTIVATE
    ```

-   The following example uses the same search parameters as example 1, but specifies “ldaps” so that a Secure LDAP connection is established with the LDAP server on host my\_LDAPserver, port 636. Only LDAP clients using the Secure LDAP protocol may now connect on this port. The database security option TRUSTED\_CERTIFICATE\_FILE must be set with a file name containing the certificate of the certificate authority \(CA\) that signed the certificate used by the LDAP server at "ldaps://my\_LDAPserver:636". During the handshake with the LDAP server, the certificate presented by the LDAP server is checked by the data lake Relational Engine server \(the LDAP client\) to ensure that it is signed by one of the certificates listed in the file. This establishes trust by the client that the server is who it says it is. The ACCESS ACCOUNT and IDENTIFIED BY parameters establish trust by the LDAP server that the client is who it says it is.

    ```
    SET OPTION PUBLIC.login_mode = 'Standard,LDAPUA'
    CREATE CERTIFICATE LDAP_CERT01 FROM 'ENTERYOURCERTIFICATEINFORMATIONHERE'
    CREATE LDAP SERVER secure_primary 
    AUTHENTICATION URL 'ldaps://my_LDAPserver:636/'
    CONNECTION TIMEOUT 3000
    TLS OFF
    WITH ACTIVATE
    
    ```

    > ### Note:  
    > The TLS parameter must be OFF when Secure LDAP is used instead of TLS protocol.


**Related Information**  


[ALTER LDAP SERVER Statement for Data Lake Relational Engine](alter-ldap-server-statement-for-data-lake-relational-engine-a425eb5.md "Any changes to an LDAP server configuration object are applied on subsequent connections. Any connection already started when the change is applied does not immediately reflect the change.")

[DROP LDAP SERVER Statement for Data Lake Relational Engine](drop-ldap-server-statement-for-data-lake-relational-engine-a426759.md "Removes the named LDAP server configuration object from the SYSLDAPSERVER system view after verifying that the LDAP server configuration object is not in a READY or ACTIVE state.")

[VALIDATE LDAP SERVER Statement for Data Lake Relational Engine](validate-ldap-server-statement-for-data-lake-relational-engine-a426f91.md "Validates changes to the settings of existing LDAP server configuration objects before applying them.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

