<!-- loioa619187d84f210158b3081e7245e94a0 -->

# CREATE SERVER Statement for Data Lake Relational Engine

Creates a remote server.



<a name="loioa619187d84f210158b3081e7245e94a0__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
CREATE SERVER <server-name> 
   CLASS '{ ASEODBC | HANAODBC| IQODBC }' 
   USING '<SQL-endpoint>;[ UseCloudConnector=[ ON | OFF ];LocationID=<cloud-connector-location-id> ]' 
   [ READ ONLY ]

```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa619187d84f210158b3081e7245e94a0__create_server_parm1"/>

## Parameters


<dl>
<dt><b>

*<SQL-endpoint\>*

</b></dt>
<dd>

The ODBC connection parameters for the remote server are dictated by the ODBC driver being used. Only TLS connections are supportedunless you are connecting through Cloud Connector using the UseCloudConnector and LocationID options. SAP recommends using TLS connections. If connecting to an on-premise database that is not using TLS through Cloud Connector, note that the connections between the on-premise database and the on-premise Cloud Connector client, as well as the cloud connectivity proxy and the data lake Relational Engine instance are not encrypted. However, the connection between the cloud connectivity proxy to the on-premise Cloud Connector client is always encrypted.



</dd>
<dd>


<dl>
<dt><b>

UseCloudConnector \[ ON | OFF \]

</b></dt>
<dd>

\(Optional\) Enables the dedicated connectivity proxy for the data lake Relational Engine instance. This allows communication between data lake Relational Engine and on-premise databases. The default value is OFF.



</dd><dt><b>

LocationID *<cloud-connector-location-id\>*

</b></dt>
<dd>

\(Optional\) Specifies the location ID of the cloud connector that will be used to open the connection. The default value is an empty string which means it will use the cloud connector which is connected without a location ID.



</dd>
</dl>



</dd><dt><b>

READ ONLY

</b></dt>
<dd>

Specifies that the remote server is a read-only data source. Any update request is rejected by data lake Relational Engine.



</dd>
</dl>



<a name="loioa619187d84f210158b3081e7245e94a0__create_server_remarks1"/>

## Remarks

CREATE SERVER defines a remote server from the data lake Relational Engine catalogs.

The value for TrustedFile must be /ase/python\_client/config/trusted.txt. This file is populated with the CREATE and DROP CERTIFICATE statement. The DigiCert Global Root CA certificate is required to connect to SAP Cloud databases. As of 2023, we sign our certificates with the DigiCert Global Root G2 certificate. We recommend that your enable your connections to trust both certificates.

> ### Note:  
> You can find details about root certificate updates on the DigiCert website at [https://knowledge.digicert.com/general-information/digicert-root-and-intermediate-ca-certificate-updates-2023](https://knowledge.digicert.com/general-information/digicert-root-and-intermediate-ca-certificate-updates-2023). Also see SAP Note [3397584](https://me.sap.com/notes/3397584), SAP Note [3327214](https://me.sap.com/notes/3327214) and SAP Note [3399573](https://me.sap.com/notes/3399573).



<a name="loioa619187d84f210158b3081e7245e94a0__IQ_Permissions"/>

## Privileges

Requires the MANAGE ANY REMOTE SERVER system privilege.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



<a name="loioa619187d84f210158b3081e7245e94a0__create_server_standards1"/>

## Standards

-   SQL – ISO/ANSI SQL compliant



<a name="loioa619187d84f210158b3081e7245e94a0__create_server_examples1"/>

## Examples

These examples create remote SAP HANA servers:

```
CREATE SERVER HDLRE2HANA CLASS 'HANAODBC' USING
     'Driver=libodbcHDB.so;
      ConnectTimeout=0;
      CommunicationTimeout=15000;
      RECONNECT=0;
      ServerNode=629934bc-6f0c-4cbf-8c58-d6cd8aef3885.hana.xxxxx.com:443;
      ENCRYPT=TRUE;
      ssltruststore=629934bc-6f0c-4cbf-8c58-d6cd8aef3885.hana.xxxxx.com;
      ssltrustcert=Yes;
      UID=DBADMIN;
      PWD=xxx'
```

```
CREATE SERVER HDLRE2HANA CLASS 'HANAODBC' USING 
     'Driver=libodbcHDB.so;
      ServerNode=hana_box2:31315;
      UID=DBADMIN;
      PWD=xxx;
      UseCloudConnector=ON'
```

To verify that the remote server is correctly configured, execute:

```
CALL sp_remote_tables('<remote-server-name>')
```

These examples create remote SAP IQ servers:

```
CREATE SERVER myIQserver CLASS 'IQODBC' USING
     'DRIVER=libdbodbc17_r.so;
      UID=HDLADMIN;
      PWD=xxx;
      host=hana_box:443;
      ENC=TLS(trusted_certificates=*;
      direct=yes;
      certificate_name=hanacloud.xxx.com);
      UseCloudConnector=ON; 
      LocationID=connector1'
```

```
CREATE SERVER myIQserver CLASS 'IQODBC' USING
     'DRIVER=libdbodbc17_r.so;
      UID=HDLADMIN;
      PWD=xxx;
      host=hana_box:2638;
      UseCloudConnector=ON; 
      LocationID=connector1'
```

```
CREATE SERVER myIQserver CLASS 'IQODBC' USING
     'DRIVER=libdbodbc17_r.so;
      UID=HDLADMIN;
      PWD=xxx;
      host=hana_box:2638;
      UseCloudConnector=ON'
```

```
CREATE SERVER myIQserver CLASS 'IQODBC' USING
     'DRIVER=libdbodbc17_r.so;
      UID=dba;
      PWD=xxx;
      commlinks=tcpip(Host=iq:6184);
      UseCloudConnector=ON; 
      LocationID=connector1'
```

To verify that the remote server is correctly configured, execute:

```
CALL sp_remote_tables('<remote-server-name>')
```

**Related Information**  


[ALTER SERVER Statement for Data Lake Relational Engine](alter-server-statement-for-data-lake-relational-engine-a613110.md "Modifies the attributes of a remote server. Changes made by ALTER SERVER do not take effect until the next connection to the remote server.")

[DROP SERVER Statement for Data Lake Relational Engine](drop-server-statement-for-data-lake-relational-engine-a61d0df.md "Drops a remote server from the data lake Relational Engine system tables.")

[CREATE EXTERNLOGIN Statement for Data Lake Relational Engine](create-externlogin-statement-for-data-lake-relational-engine-a61766a.md "Assigns an alternate login name and password to be used when communicating with a remote server.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[Create an SAP HANA On-Premise Remote Server](https://help.sap.com/viewer/a8937bea84f21015a80bc776cf758d50/2024_3_QRC/en-US/494a8b264b8e4dfa8fc9b095324191b3.html "Create a remote server to an SAP HANA on-premise database from data lake Relational Engine.") :arrow_upper_right:

[Create an SAP IQ On-Premise Remote Server](https://help.sap.com/viewer/a8937bea84f21015a80bc776cf758d50/2024_3_QRC/en-US/7fa7b84a61bd4312a55f7a68be8dd4a9.html "Create a remote server to an SAP IQ on-premise database from data lake Relational Engine.") :arrow_upper_right:

[HANA ODBC Connection Properties](https://help.sap.com/docs/SAP_HANA_CLIENT/f1b440ded6144a54ada97ff95dac7adf/7cab593774474f2f8db335710b2f5c50.html)

[\(IQ ODBC\) Connection Parameters](https://help.sap.com/docs/SAP_IQ/8e6989ea146b41d78f671443295cd7a0/a6d47d6e84f210158d4980b069eff5dd.html)

