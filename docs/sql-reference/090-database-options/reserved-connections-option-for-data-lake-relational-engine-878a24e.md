<!-- loio878a24e0145b409a92647b8673bea416 -->

# RESERVED\_CONNECTIONS Option for Data Lake Relational Engine

Controls the minimum number of concurrent connections that a database must reserve for standard connections. This option is useful when your database server accepts HTTP/HTTPS connections.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loio878a24e0145b409a92647b8673bea416__section_zx3_g24_hrb"/>

## Syntax

```
RESERVED_CONNECTIONS = <value>
```



## Allowed Values

 size
 :   This integer specifies the number of concurrent connections that the database must reserve for standard connections.

    For databases running on the network database server, specify a number that fulfills the following requirements:

    -   Less than the maximum database server connection limit as specified by the -gm database server option.

    -   Less than the maximum database connection limit specified by the max\_connections database option.

 

Requires a restart of the database service, using SAP HANA Cloud Central, for the change to take effect.



## Scope


<table>
<tr>
<th valign="top">

 



</th>
<th valign="top">

PUBLIC role



</th>
<th valign="top">

For current user



</th>
<th valign="top">

For other users



</th>
</tr>
<tr>
<td valign="top">

Allowed to set permanently?



</td>
<td valign="top">

Yes



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
</tr>
<tr>
<td valign="top">

Allowed to set temporarily?



</td>
<td valign="top">

Yes



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
</tr>
</table>



## Remarks

Setting this option ensures that a database can accept standard connections even when its HTTP/HTTPS connections are queued.

A database server accepts HTTP/HTTPS connections until it reaches its limit, and then it queues subsequent HTTP/HTTPS connections and processes them as connections are made available. There is no opportunity for a standard connection to replace an HTTP/HTTPS connection while there are connection attempts in the queue. Users wanting to make a standard connection, could wait indefinitely for the HTTP/HTTPS connection queue to complete. Use the reserved\_connections option to specify a minimum number of database connections that can only accept standard connections.

By default, the network database server does not reserve connections.

You can view the current number of reserved connections for a database by querying the value of the reserved\_connections connection property:

```
SELECT CONNECTION_PROPERTY ( 'reserved_connections' );
```



## Example

The following example reserves 10 connections for standard connections.

```
SET OPTION PUBLIC.reserved_connections=10;
```

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

