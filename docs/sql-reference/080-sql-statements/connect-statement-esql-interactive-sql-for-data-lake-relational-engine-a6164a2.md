<!-- loioa6164a2584f210158b79b517cd3c0491 -->

# CONNECT Statement \[ESQL\] \[Interactive SQL\] for Data Lake Relational Engine

Establishes a connection to the database identified by *<database-name\>* running on the server identified by *<engine-name\>*.



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.




<dl>
<dt><b>

Syntax 1

</b></dt>
<dd>

```
CONNECT
   …[ TO <engine-name> ]
   …[ DATABASE <database-name> ]
   …[ AS <connection-name> ]
   …[ USER ] <userid> [ IDENTIFIED BY ]
```



</dd><dt><b>

Syntax 2

</b></dt>
<dd>

```
CONNECT USING <connect-string>
```



</dd>
</dl>



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa6164a2584f210158b79b517cd3c0491__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

AS *<connection-name\>*

</b></dt>
<dd>

Connection can optionally be named by specifying the clause. This allows multiple connections to the same database, or multiple connections to the same or different database servers, all simultaneously. Each connection has its own associated transaction. You might even get locking conflicts between your transactions if, for example, you try to modify the same record in the same database from two different connections.



</dd><dt><b>

*<connect-string\>*

</b></dt>
<dd>

A list of parameter settings of the form keyword=*<value\>*, and must be enclosed in single quotes.



</dd>
</dl>



<a name="loioa6164a2584f210158b79b517cd3c0491__IQ_Usage"/>

## Remarks


<dl>
<dt><b>

Embedded SQL behavior

</b></dt>
<dd>

If no *<engine-name\>* is specified, the default local database server is assumed \(the first database server started\). If no *<database-name\>* is specified, the first database on the given server is assumed.

The user ID and password are used for permission checks on all dynamic SQL statements. By default, the password is case-sensitive; the user ID is not. You can connect without a password by using a host variable for the password and setting the value of the host variable to be the null pointer.



</dd><dt><b>

Dbisql behavior

</b></dt>
<dd>

If no database or server is specified in the CONNECT statement, dbisql remains connected to the current database, rather than to the default server and database. If a database name is specified without a server name, dbisql attempts to connect to the specified database on the current server. You must specify the database name defined in the -n database switch, not the database file name. If a server name is specified without a database name, dbisql connects to the default database on the specified server. For example, if this batch is executed while connected to a database, the two tables are created in the same database:

```
CREATE TABLE t1( c1 int );
CONNECT HDLADMIN IDENTIFIED BY <password>;
CREATE TABLE t2 ( c1 int );
```

No other database statements are allowed until a successful CONNECT statement has been executed.

The user ID and password check the permissions on SQL statements. If the password or the user ID and password are not specified, the user is prompted to type the missing information. By default, the password is case-sensitive; the user ID is not.



</dd>
</dl>

Multiple connections are managed through the concept of a current connection. After a successful connect statement, the new connection becomes the current one. To switch to a different connection, use SET CONNECTION. Executing a CONNECT statement does not close the existing connection \(if any\). Use DISCONNECT to drop connections.

Static SQL statements use the user ID and password specified with the -l option on the SQLPP statement line. If no -l option is given, the user ID and password of the CONNECT statement are used for static SQL statements also.



<a name="loioa6164a2584f210158b79b517cd3c0491__IQ_Permissions"/>

## Privileges

None



<a name="loioa6164a2584f210158b79b517cd3c0491__IQ_Standards"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa6164a2584f210158b79b517cd3c0491__IQ_Examples"/>

## Examples

-   The following example connects to the default database using dbisql without specifying credentials. You are prompted for a user ID and password:

    ```
    CONNECT
    ```

-   The following example connects to the default database as user HDLADMIN using . You are prompted for a user ID and password:

    ```
    CONNECT USER "HDLADMIN"
    ```

-   The following example connects to the demo database as user HDLADMIN using dbisql, where *<machine\_iqdemo\>* is the engine name:

    ```
    CONNECT 
    TO <machine_iqdemo>
    USER "HDLADMIN"
    IDENTIFIED BY <password>
    ```

-   The following example connects to the demo database using a connect string using dbisql:

    ```
    CONNECT USING 'UID=HDLADMIN;PWD=<password>;DBN=iqdemo'
    ```


**Related Information**  


[DISCONNECT Statement \[Interactive SQL\] for Data Lake Relational Engine](disconnect-statement-interactive-sql-for-data-lake-relational-engine-a61bf2a.md "Drops a connection with the database.")

[GRANT CONNECT Statement for Data Lake Relational Engine](grant-connect-statement-for-data-lake-relational-engine-a3e04cc.md "Create a new user, and can also be used to change a password. However, it is recommended that you use the CREATE USER statement to create users instead of the GRANT CONNECT statement.")

[SET CONNECTION Statement \[ESQL\] \[Interactive SQL\] for Data Lake Relational Engine](set-connection-statement-esql-interactive-sql-for-data-lake-relational-engine-a6257ba.md "Changes the active database connection.")

