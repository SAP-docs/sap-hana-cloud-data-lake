<!-- loioa602ced184f210158c90b4b833754412 -->

# CREATE TEXT INDEX Statement for Data Lake Relational Engine

Creates a TEXT index and specifies the text configuration object to use.



<a name="loioa602ced184f210158c90b4b833754412__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
CREATE TEXT INDEX <text-index-name>
   ON [ { <owner> | <schema-name> }]<table-name>( <column-name>,
   [ CONFIGURATION [ <owner>]<text-configuration-name>]
   [ IMMEDIATE REFRESH ]
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa602ced184f210158c90b4b833754412__IQ_Parameters"/>

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



<a name="loioa602ced184f210158c90b4b833754412__IQ_Usage"/>

## Remarks

You cannot create a TEXT index on views or temporary tables, or on an IN SYSTEM materialized view. The BEGIN PARALLEL IQ…END PARALLEL IQ statement does not support CREATE TEXT INDEX.



<a name="loioa602ced184f210158c90b4b833754412__IQ_Permissions"/>

## Privileges

-   You own the underlying table of the index.
-   REFERENCES object-level privilege on the table.
-   CREATE ANY INDEX system privilege
-   CREATE ANY OBJECT system privilege
-   CREATE ANY or REFERENCES object-level privilege on the schema containing the underlying table if the schema owned by another user.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) or [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md) for assistance with granting privileges.



<a name="loioa602ced184f210158c90b4b833754412__side_effects"/>

## Side Effects

Automatic commit



<a name="loioa602ced184f210158c90b4b833754412__IQ_Examples"/>

## Examples

The following example creates a TEXT index, `myTxtIdx`, on the `CompanyName` column of the `Customers` table, using the `max_term_sixteen` text configuration object:

```
CREATE TEXT INDEX myTxtIdx ON Customers (CompanyName );
```

```
CONFIGURATION max_term_sixteen;
```

**Related Information**  


[CREATE INDEX Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/afc9ba646bb842d6b4c5975aa7d17d16.html "Creates an index on a specified table, or pair of tables. Once an index is created, it is never referenced in a SQL statement again except to delete it using the DROP INDEX statement.") :arrow_upper_right:

[ALTER TEXT INDEX Statement for Data Lake Relational Engine](alter-text-index-statement-for-data-lake-relational-engine-a602711.md "Renames, moves or alters the definition of a TEXT index.")

[DROP TEXT INDEX Statement for Data Lake Relational Engine](drop-text-index-statement-for-data-lake-relational-engine-a60331d.md "Removes a TEXT index from the database.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[REVOKE Object-Level Privilege Statement for Data Lake Relational Engine](revoke-object-level-privilege-statement-for-data-lake-relational-engine-a3e7af2.md "Removes object-level privileges that were given using the GRANT statement.")

