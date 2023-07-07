<!-- loioa425eb5084f21015be10c7391eef4df1 -->

# ALTER LDAP SERVER Statement for Data Lake Relational Engine

Any changes to an LDAP server configuration object are applied on subsequent connections. Any connection already started when the change is applied does not immediately reflect the change.



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
ALTER LDAP SERVER <ldapua-server-name> 
   [ { SEARCH DN
      { URL { '<URL_string>' | NULL } 
         | ACCESS ACCOUNT { '<DN_string>' | NULL } 
         | IDENTIFIED BY { '<password>' | NULL }
      | AUTHENTICATION URL { '<URL_string>' | NULL } 
      | CONNECTION TIMEOUT <timeout_value> 
      | CONNECTION RETRIES <retry_value> 
      | TLS OFF }  ]
   [ WITH ( { SUSPEND | ACTIVATE | REFRESH } ) ]
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa425eb5084f21015be10c7391eef4df1__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

URL '*<URL\_string\>*'

</b></dt>
<dd>

Identifies the host \(by name or by IP address\), port number, and the search to be performed for the DN lookup for a given user ID. This value is validated for correct LDAP URL syntax before it is stored in the ISYSLDAPSERVER system table. The maximum size for this string is 1024 bytes.



</dd><dt><b>

ACCESS ACCOUNT \{ '*<DN\_string\>*' | NULL \}

</b></dt>
<dd>

User created in the LDAP server for use by data lake Relational Engine, not a user within data lake Relational Engine. The distinguished name \(DN\) for this user is used to connect to the LDAP server. This user has permissions within the LDAP server to search for DNs by user ID in the locations specified by the SEARCH DN URL. The maximum size for this string is 1024 bytes.



</dd>
</dl>


<dl>
<dt><b>

IDENTIFIED BY \{ '*<password\>*' | NULL \}

</b></dt>
<dd>

Provides the password associated with the ACCESS ACCOUNT user. The password is stored using symmetric encryption on disk. Use the value NULL to clear the password and set it to none. The maximum size of a clear text password is 255 bytes.



</dd><dt><b>

AUTHENTICATION URL \{ '*<URL\_string\>*' | NULL \}

</b></dt>
<dd>

Identifies the host \(by name or IP address\) and the port number of the LDAP server to use for authentication of the user. This is the value defined for URL\_string and is validated for correct LDAP URL syntax before it is stored in `ISYSLDAPSERVER` system table. The DN of the user obtained from a prior DN search and the user password bind a new connection to the authentication URL. A successful connection to the LDAP server is considered proof of the identity of the connecting user. The maximum size for this string is 1024 bytes.



</dd><dt><b>

CONNECTION TIMEOUT *<timeout\_value\>*

</b></dt>
<dd>

Identifies the host \(by name or IP address\) and the port number of the LDAP server to use for authentication of the user. This is the value defined for URL\_string and is validated for correct LDAP URL syntax before it is stored in `ISYSLDAPSERVER` system table. The DN of the user obtained from a prior DN search and the user password bind a new connection to the authentication URL. A successful connection to the LDAP server is considered proof of the identity of the connecting user. The maximum size for this string is 1024 bytes.



</dd><dt><b>

CONNECTION RETRIES *<retry\_value\>*

</b></dt>
<dd>

Specifies the number of retries on connections from data lake Relational Engine to the LDAP server for both DN searches and authentication. The valid range of values is 1– 60, with a default value of 3.



</dd><dt><b>

TLS OFF

</b></dt>
<dd>

Defines whether the TLS or Secure LDAP protocol is used for connections to the LDAP server for both DN searches and authentication. When set to OFF \(or not specified\), Secure LDAP protocol is used and the URL begins with “ldaps://”. When using the TLS protocol, specify the database security option TRUSTED\_CERTIFICATES\_FILE with a file name containing the certificate of the Certificate Authority \(CA\) that signed the certificate used by the LDAP server.



</dd><dt><b>

WITH ACTIVATE

</b></dt>
<dd>

Activates the LDAP server configuration object for immediate use upon creation. This permits the definition and activation of LDAP User Authentication in one statement. The LDAP server configuration object state changes to READY when WITH ACTIVATE is used.



</dd>
</dl>



<a name="loioa425eb5084f21015be10c7391eef4df1__IQ_Usage"/>

## Remarks

In addition to resetting LDAP server configuration object values for attributes, the `ALTER LDAP SERVER` statement allows an administrator to make manual adjustments to a server's state and behavior by putting the LDAP server configuration object in maintenance mode and returning it to service from maintenance mode.



<a name="loioa425eb5084f21015be10c7391eef4df1__IQ_Permissions"/>

## Privileges

Requires the MANAGE ANY LDAP SERVER system privilege.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



<a name="loioa425eb5084f21015be10c7391eef4df1__IQ_Standards"/>

## Standards

ANSI SQL – compliance level: Transact-SQL extension



<a name="loioa425eb5084f21015be10c7391eef4df1__IQ_Examples"/>

## Examples

-   The following example suspends the LDAP server configuration object named `apps_primary`:

    ```
    ALTER LDAP SERVER apps_primary SUSPEND
    ```

-   The following example changes  the  LDAP server  configuration object named `apps_primary` to use a different URL for authentication on host `fairfax`, sets the port number to `1066`, sets the number of connection retries to `10`, and finally activates the LDAP server configuration object:

    ```
    ALTER LDAP SERVER apps_primary
    AUTHENTICATION URL 'ldaps://my_LDAPserver:1066/'
    CONNECTION RETRIES 10
    WITH ACTIVATE
    ```


**Related Information**  


[CREATE LDAP SERVER Statement for Data Lake Relational Engine](create-ldap-server-statement-for-data-lake-relational-engine-a424e90.md "Creates a new LDAP server configuration object for LDAP user authentication. Parameters defined during the creation of an LDAP server configuration object are stored in the ISYSLDAPSERVER (system view SYSLDAPSERVER) system table.")

[DROP LDAP SERVER Statement for Data Lake Relational Engine](drop-ldap-server-statement-for-data-lake-relational-engine-a426759.md "Removes the named LDAP server configuration object from the SYSLDAPSERVER system view after verifying that the LDAP server configuration object is not in a READY or ACTIVE state.")

[VALIDATE LDAP SERVER Statement for Data Lake Relational Engine](validate-ldap-server-statement-for-data-lake-relational-engine-a426f91.md "Validates changes to the settings of existing LDAP server configuration objects before applying them.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

