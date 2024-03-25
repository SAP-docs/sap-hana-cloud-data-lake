<!-- loioed8c66421c154ebea93418092bbbcd6e -->

# DROP DATATYPE Statement for Data Lake Relational Engine

Removes a data type from the database.



<a name="loioed8c66421c154ebea93418092bbbcd6e__section_azh_5fj_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
DROP DATATYPE <datatype-name>
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioed8c66421c154ebea93418092bbbcd6e__IQ_Usage"/>

## Remarks

None



<a name="loioed8c66421c154ebea93418092bbbcd6e__drop_datatype_privileges1"/>

## Privileges

Requires you own the message.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) or [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md) for assistance with granting privileges.



<a name="loioed8c66421c154ebea93418092bbbcd6e__IQ_Side_Effects"/>

## Side Effects

-   Automatic commit. Clears the Data window in dbisql.



<a name="loioed8c66421c154ebea93418092bbbcd6e__IQ_Standards"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products – supported by SAP Adaptive Server Enterprise



<a name="loioed8c66421c154ebea93418092bbbcd6e__IQ_Examples"/>

## Examples

This example drops the dataytpe phonenum1:

```
DROP DATATYPE phonenum1;
```

**Related Information**  


[CREATE DOMAIN Statementfor Data Lake Relational Engine](create-domain-statementfor-data-lake-relational-engine-a616d8e.md "Creates a user-defined data type in the database.")

