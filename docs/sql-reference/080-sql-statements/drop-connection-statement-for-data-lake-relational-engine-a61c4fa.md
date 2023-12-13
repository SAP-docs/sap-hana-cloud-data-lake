<!-- loioa61c4fa184f21015b43ac105d9d73fe2 -->

# DROP CONNECTION Statement for Data Lake Relational Engine

Drops any user connection to the database.



<a name="loioa61c4fa184f21015b43ac105d9d73fe2__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
DROP CONNECTION <connection-id>;
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa61c4fa184f21015b43ac105d9d73fe2__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

*<connection-id\>*

</b></dt>
<dd>

Obtained using the `CONNECTION_PROPERTY` function to request the connection number. This statement returns the connection ID of the current connection:

```
SELECT connection_property( 'number' );
```



</dd>
</dl>



<a name="loioa61c4fa184f21015b43ac105d9d73fe2__IQ_Usage"/>

## Remarks

You cannot drop your current connection; you must first create another connection, then drop your first connection.



<a name="loioa61c4fa184f21015b43ac105d9d73fe2__IQ_Permissions"/>

## Privileges

Requires the DROP ANY CONNECTION system privilege.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



<a name="loioa61c4fa184f21015b43ac105d9d73fe2__IQ_Standards"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loioa61c4fa184f21015b43ac105d9d73fe2__IQ_Examples"/>

## Examples

The following example drops the connection with ID number 4:You cannot drop your current connection; you must first create another connection, then drop your first connection.

```
DROP CONNECTION 4;
```

**Related Information**  


[CONNECT Statement \[ESQL\] \[Interactive SQL\] for Data Lake Relational Engine](connect-statement-esql-interactive-sql-for-data-lake-relational-engine-a6164a2.md "Establishes a connection to the database identified by database-name running on the server identified by engine-name.")

[CONNECTION\_PROPERTY Function \[System\] for Data Lake Relational Engine](../050-system-sql-functions/connection-property-function-system-for-data-lake-relational-engine-a53eeaf.md "Returns the value of a given connection property as a string.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

