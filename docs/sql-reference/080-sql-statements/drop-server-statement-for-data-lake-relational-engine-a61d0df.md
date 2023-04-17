<!-- loioa61d0df184f210159743882739ec29d0 -->

# DROP SERVER Statement for Data Lake Relational Engine

Drops a remote server from the data lake Relational Engine system tables.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
DROP SERVER <server-name>
```



<a name="loioa61d0df184f210159743882739ec29d0__drop_server_remarks1"/>

## Remarks

Before `DROP SERVER` succeeds, drop all the proxy tables that have been defined for the remote server.



<a name="loioa61d0df184f210159743882739ec29d0__IQ_Permissions"/>

## Privileges

Requires the MANAGE ANY REMOTE SERVER system privilege.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



<a name="loioa61d0df184f210159743882739ec29d0__drop_server_sideefects1"/>

## Side Effects

Automatic commit



<a name="loioa61d0df184f210159743882739ec29d0__drop_server_standards1"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products – supported by Open Client/Open Server



<a name="loioa61d0df184f210159743882739ec29d0__drop_server_examples1"/>

## Examples

The following example drops the server `IQ_prod`:

```
DROP SERVER iq_prod
```

**Related Information**  


[CREATE SERVER Statement for Data Lake Relational Engine](create-server-statement-for-data-lake-relational-engine-a619187.md "Creates a remote server.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

