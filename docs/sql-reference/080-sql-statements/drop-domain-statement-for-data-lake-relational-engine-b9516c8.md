<!-- loiob9516c87e589469facab1deaca3e4ebb -->

# DROP DOMAIN Statement for Data Lake Relational Engine

Removes a domain \(data type\) from the database.



<a name="loiob9516c87e589469facab1deaca3e4ebb__section_azh_5fj_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
DROP DOMAIN <domain-name>
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loiob9516c87e589469facab1deaca3e4ebb__IQ_Usage"/>

## Remarks

DROP DOMAIN is prevented if the data type is used in a table column, or in a procedure or function argument. You must change data types on all columns defined using the domain to drop the data type. It is recommended that you use DROP DOMAIN rather than DROP DATATYPE, as DROP DOMAIN is the syntax used in the ANSI/ISO SQL Standard. You cannot drop system-defined data types \(such as MONEY or UNIQUEIDENTIFIERSTR\) from a database.



<a name="loiob9516c87e589469facab1deaca3e4ebb__drop_datatype_privileges1"/>

## Privileges

-   Requires one of:
    -   You own the object
    -   DROP DATATYPE system privilege


See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) or [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md) for assistance with granting privileges.



<a name="loiob9516c87e589469facab1deaca3e4ebb__IQ_Side_Effects"/>

## Side Effects

-   Automatic commit. Clears the Data window in dbisql.



<a name="loiob9516c87e589469facab1deaca3e4ebb__IQ_Standards"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products – supported by SAP Adaptive Server Enterprise



<a name="loiob9516c87e589469facab1deaca3e4ebb__IQ_Examples"/>

## Examples

This example drops the domain custphonenum1:

```
DROP DOMAIN custphonenum1;
```

**Related Information**  


[CREATE DOMAIN Statement for Data Lake Relational Engine](create-domain-statement-for-data-lake-relational-engine-a616d8e.md "Creates a user-defined data type in the database.")

