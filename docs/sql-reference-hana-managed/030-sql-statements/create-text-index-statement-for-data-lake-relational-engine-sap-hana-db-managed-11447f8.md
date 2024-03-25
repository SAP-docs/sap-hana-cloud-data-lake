<!-- loio11447f8825504a4b8cc578f3204aec12 -->

# CREATE TEXT INDEX Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Creates a TEXT index.



<a name="loio11447f8825504a4b8cc578f3204aec12__section_wnl_ffg_s1c"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:

-   Connected to SAP HANA database as a SAP HANA database user..



```
CREATE TEXT INDEX <text-index-name>
   ON [ { <owner> | <schema-name> }]<table-name>( <column-name>,
   [ CONFIGURATION [ <owner>]<text-configuration-name>]
   [ IMMEDIATE REFRESH ]
```



## Parameters


<dl>
<dt><b>

ON

</b></dt>
<dd>

Specifies the table and column on which to build the TEXT index.



</dd><dt><b>

CONFIGURATION

</b></dt>
<dd>

Specifies the text configuration object to use when creating the TEXT index. If this clause is not specified, the default\_char text configuration object is used.



</dd><dt><b>

IMMEDIATE REFRESH

</b></dt>
<dd>

\(Default\) refreshes the TEXT index each time changes in the underlying table impact data in the TEXT index. Only permitted value for tables in data lake Relational Engine main store. Once created, the IMMEDIATE REFRESH clause cannot be changed.



</dd>
</dl>



## Remarks

You cannot create a TEXT index on views or temporary tables, or on an IN SYSTEM materialized view. The BEGIN PARALLEL IQ…END PARALLEL IQ statement does not support CREATE TEXT INDEX.



## Privileges

-   You own the underlying table of the index.
-   REFERENCES object-level privilege on the table.
-   CREATE ANY INDEX system privilege
-   CREATE ANY OBJECT system privilege
-   CREATE ANY or REFERENCES object-level privilege on the schema containing the underlying table if the schema owned by another user.

See [GRANT System Privilege Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/a3dfcb0284f21015b74ac3cded42ee69.html "Grants specific system privileges to users or roles, with or without administrative rights.") :arrow_upper_right: or [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/a3e154f084f21015996d891a5e9d33d2.html "Grants database object-level privileges on individual objects and schemas to a user or role.") :arrow_upper_right: for assistance with granting privileges.



## Side Effects

Automatic commit



## Examples

The following example creates a TEXT index, myTxtIdx, on the CompanyName column of the Customers table.

```
CREATE TEXT INDEX myTxtIdx ON Customers (CompanyName );
```

**Related Information**  


[CREATE INDEX Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/a617ca4484f21015b2cdfdebbf4a5eee.html "Creates an index on a specified table, or pair of tables. Once an index is created, it is never referenced in a SQL statement again except to delete it using the DROP INDEX statement.") :arrow_upper_right:

[CREATE TEXT INDEX Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/a602ced184f210158c90b4b833754412.html "Creates a TEXT index and specifies the text configuration object to use.") :arrow_upper_right:

