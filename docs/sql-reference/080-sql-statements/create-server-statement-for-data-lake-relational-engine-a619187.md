<!-- loioa619187d84f210158b3081e7245e94a0 -->

# CREATE SERVER Statement for Data Lake Relational Engine

Creates a remote server.



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
CREATE SERVER <server-name> 
   CLASS '{ ASEODBC | HANAODBC | ODBC | IQODBC }' 
   USING '<SQL_endpoint>' 
   [ READ ONLY ]
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa619187d84f210158b3081e7245e94a0__create_server_parm1"/>

## Parameters


<dl>
<dt><b>

*<SQL\_endpoint\>*

</b></dt>
<dd>

The ODBC connection parameters for the remote server are dictated by the ODBC driver being used. Only TLS connections are supported.



</dd><dt><b>

READ ONLY

</b></dt>
<dd>

Specifies that the remote server is a read-only data source. Any update request is rejected by data lake Relational Engine.



</dd>
</dl>



<a name="loioa619187d84f210158b3081e7245e94a0__create_server_remarks1"/>

## Remarks

`CREATE SERVER` defines a remote server from the data lake Relational Engine catalogs.

The value for TrustedFile must be /ase/python\_client/config/trusted.txt. This file is populated with the CREATE and DROP CERTIFICATE statement. The DigiCertRootCA is required to connect to SAP Cloud databases.



<a name="loioa619187d84f210158b3081e7245e94a0__IQ_Permissions"/>

## Privileges

Requires the MANAGE ANY REMOTE SERVER system privilege.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



<a name="loioa619187d84f210158b3081e7245e94a0__create_server_standards1"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products – supported by Open Client/Open Server



<a name="loioa619187d84f210158b3081e7245e94a0__create_server_examples1"/>

## Examples

This example creates a remote HANA server:

```
CREATE SERVER myHANAserver CLASS 'HANAODBC' USING 
   'CREATE SERVER HC CLASS 'HANAODBC' USING
'Driver=/datadrive/hdbclient/libodbcHDB.so;
ConnectTimeout=0;
CommunicationTimeout=15000;
RECONNECT=0;
ServerNode=629934bc-6f0c-4cbf-8c58-d6cd8aef3885.hana.xxxxx.com:443;
ENCRYPT=TRUE;
ssltruststore=629934bc-6f0c-4cbf-8c58-d6cd8aef3885.hana.xxxxx.com;
ssltrustcert=Yes;
UID=DBADMIN;PWD=xxx;'
```

This example creates a remote IQ server:

```
CREATE SERVER myIQserver CLASS 'IQODBC' USING
   'DRIVER=libdbodbc17_r.so;
    UID=HDLADMIN;PWD=xxx;
    host=d0aeefbf-7075-49cd-b827-812cd947655e.xxx.com:443;
   ENC=TLS(trusted_certificates=*;direct=yes;certificate_name=hanacloud.xxx.com)'
```

This example creates a remote ASE cloud server:

```
CREATE SERVER myASEserver  CLASS 'ASEODBC' USING 
   'Driver=libsybdrvodb.so;TrustedFile=/ase/python_client/config/trusted.txt;
   Server=zasebenss001.ase.xxx.com;
   Port=443;Encryption=ssl';
```

**Related Information**  


[ALTER SERVER Statement for Data Lake Relational Engine](alter-server-statement-for-data-lake-relational-engine-a613110.md "Modifies the attributes of a remote server. Changes made by ALTER SERVER do not take effect until the next connection to the remote server.")

[DROP SERVER Statement for Data Lake Relational Engine](drop-server-statement-for-data-lake-relational-engine-a61d0df.md "Drops a remote server from the data lake Relational Engine system tables.")

[CREATE EXTERNLOGIN Statement for Data Lake Relational Engine](create-externlogin-statement-for-data-lake-relational-engine-a61766a.md "Assigns an alternate login name and password to be used when communicating with a remote server.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

