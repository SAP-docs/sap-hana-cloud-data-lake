<!-- loiobf9d79062d4b43c0aaefba8222c8421d -->

# DROP PROCEDURE Statement for Data Lake Relational Engine

Removes a user-defined procedure from the database.



<a name="loiobf9d79062d4b43c0aaefba8222c8421d__section_azh_5fj_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
DROP PROCEDURE [ IF EXISTS ] [ { <owner> | <schema-name> }.]<procedure-name>
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loiobf9d79062d4b43c0aaefba8222c8421d__drop_procedure_param1"/>

## Parameters


<dl>
<dt><b>

IF EXISTS

</b></dt>
<dd>

Use if you do not want an error returned when the DROP statement attempts to remove a database object that does not exist.



</dd>
</dl>



<a name="loiobf9d79062d4b43c0aaefba8222c8421d__drop_procedure_remarks1"/>

## Remarks

DROP PROCEDURE is prevented when the procedure is in use by another connection.



<a name="loiobf9d79062d4b43c0aaefba8222c8421d__drop_procedure_priv1"/>

## Privileges



### 

-   Requires one of:
    -   You own the procedure.
    -   DROP ANY PROCEDURE system privilege
    -   DROP ANY OBJECT system privilege
    -   DROP object-level privilege on the procedure
    -   DROP object-level privilege on the schema containing the procedure if the schema is owned by another user.


See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) or [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md) for assistance with granting privileges.



<a name="loiobf9d79062d4b43c0aaefba8222c8421d__drop_procedure_side_effects1"/>

## Side Effects

-   Automatic commit. Clears the Data window in dbisql.



<a name="loiobf9d79062d4b43c0aaefba8222c8421d__drop_procedure_examples1"/>

## Examples

This example drops a procedure called myprocedure1.

```
DROP PROCEDURE myprocedure1;
```

**Related Information**  


[ALTER PROCEDURE Statement for Data Lake Relational Engine](alter-procedure-statement-for-data-lake-relational-engine-a612e25.md "Replaces an existing procedure with a modified version. Include the entire modified procedure in the ALTER PROCEDURE statement, and reassign user permissions on the procedure.")

[CREATE PROCEDURE Statement for Data Lake Relational Engine](create-procedure-statement-for-data-lake-relational-engine-a6185b2.md "Creates a new user-defined SQL procedure in the database.")

[DROP PROCEDURE Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/86898fa1ad8546c58b0dfa704077a491.html "Removes a user-defined procedure from the database.") :arrow_upper_right:

