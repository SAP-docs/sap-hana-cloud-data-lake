<!-- loioa613110184f210158bab9d8f4e953fe1 -->

# ALTER SERVER Statement for Data Lake Relational Engine

Modifies the attributes of a remote server. Changes made by `ALTER SERVER` do not take effect until the next connection to the remote server.



<a name="loioa613110184f210158bab9d8f4e953fe1__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
ALTER SERVER <server-name> 
   [ CLASS '{ ASEODBC | HANAODBC | ODBC | IQODBC }' ]
   [ USING '<SQL_endpoint>' ]
   [ CAPABILITY '<cap-name>' { ON | OFF } ]
   [ CONNECTION CLOSE [ CURRENT | ALL | <connection-id> ] ];
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa613110184f210158bab9d8f4e953fe1__alter_server_parm1"/>

## Parameters


<dl>
<dt><b>

*<SQL\_endpoint\>*

</b></dt>
<dd>

The ODBC connection parameters for the remote server are dictated by the ODBC driver being used. Only TLS connections are supported.



</dd><dt><b>

CAPABILITY '' \{ ON | OFF \}

</b></dt>
<dd>

Turns a server capability ON or OFF. Server capabilities are stored in the system table SYSCAPABILITY. The names of these capabilities are stored in the system table SYSCAPABILITYNAME. The SYSCAPABILITY table contains no entries for*<cap-name\>* a remote server until the first connection is made to that server. At the first connection, data lake Relational Engine interrogates the server about its capabilities and then populates SYSCAPABILITY. For subsequent connections, the server’s capabilities are obtained from this table.

In general, you need not alter a server’s capabilities. It might be necessary to alter capabilities of a generic server of class ODBC.

*<cap-name\>* is the name of a server capability



</dd><dt><b>

CONNECTION CLOSE \[ CURRENT | ALL | *<connection-id\>* \]

</b></dt>
<dd>

When a user creates a connection to a remote server, the remote connection is not closed until the user disconnects from the local database. The CONNECTION CLOSE clause allows you to explicitly close connections to a remote server. You may find this useful when a remote connection becomes inactive or is no longer needed.

These SQL statements are equivalent and close the current connection to the remote server:

```
ALTER SERVER <server-name> CONNECTION CLOSE;
```

```
ALTER SERVER <server-name> CONNECTION CLOSE CURRENT;
```

You can close both ODBC and JDBC connections to a remote server using this syntax. You do not need the MANAGE ANY REMOTE SERVER system privilege to execute either of these statements.

You can also disconnect a specific remote ODBC connection by specifying a connection ID, or disconnect all remote ODBC connections by specifying the ALL keyword. If you attempt to close a JDBC connection by specifying the connection ID or the ALL keyword, an error occurs. When the connection identified by *<connection-id\>* is not the current local connection, the user must have the MANAGE ANY REMOTE SERVER system privilege to be able to close the connection.



</dd>
</dl>



<a name="loioa613110184f210158bab9d8f4e953fe1__IQ_Permissions"/>

## Privileges

Requires the MANAGE ANY REMOTE SERVER system privilege.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



<a name="loioa613110184f210158bab9d8f4e953fe1__alter_server_sideefects1"/>

## Side Effects

Automatic commit



<a name="loioa613110184f210158bab9d8f4e953fe1__alter_server_standards1"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – supported by Open Client/Open Server



<a name="loioa613110184f210158bab9d8f4e953fe1__alter_server_examples1"/>

## Examples

-   The following example changes a capability of server `infodc`:

    ```
    ALTER SERVER infodc
    CAPABILITY 'insert select' OFF;
    ```

-   The following example closes all connections to the remote server named `rem_test`:

    ```
    ALTER SERVER rem_test
    CONNECTION CLOSE ALL;
    ```

-   The following example closes the connection to the remote server named `rem_test` that has the connection ID 142536:

    ```
    ALTER SERVER rem_test
    CONNECTION CLOSE 142536;
    ```


**Related Information**  


[CREATE SERVER Statement for Data Lake Relational Engine](create-server-statement-for-data-lake-relational-engine-a619187.md "Creates a remote server.")

[DROP SERVER Statement for Data Lake Relational Engine](drop-server-statement-for-data-lake-relational-engine-a61d0df.md "Drops a remote server from the data lake Relational Engine system tables.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

