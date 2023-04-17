<!-- loio86898fa1ad8546c58b0dfa704077a491 -->

# DROP PROCEDURE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Removes user-defined procedures from the database.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Executing SQL Statements](remote-execute-usage-examples-for-executing-sql-statements-fd99ac0.md).
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
DROP PROCEDURE [ IF EXISTS ] [ [/pandoc/div/div/horizontalrule/codeblock/span/span
     {""}) [/pandoc/div/div/horizontalrule/codeblock/span/span/varname
     {"varname"}) <schema-name> (varname] (span].][/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <procedure-name> (varname]
```



<a name="loio86898fa1ad8546c58b0dfa704077a491__IQ_Parameters"/>

## Parameters

 IF EXISTS
 :   Prevents the return of an error if the specified procedure does not exist.

 

<a name="loio86898fa1ad8546c58b0dfa704077a491__section_yn4_lgq_lnb"/>

## Privileges

The privileges required depend on your data lake Relational Engine \(SAP HANA DB-Managed\) connection method:

 Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure:
 :   You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).

  Connected directly to data lake Relational Engine as a data lake Relational Engine user:
 :   -   Requires one of:
    -   You own the procedure
    -   DROP ANY PROCEDURE system privilege
    -   DROP ANY OBJECT system privilege
    -   DROP object-level privilege on the procedure
    -   DROP object-level privilege on the schema containing the procedure if the schema is owned by another user.


 

<a name="loio86898fa1ad8546c58b0dfa704077a491__section_cfp_5ds_4mb"/>

## Remarks

You cannot drop a procedure that is in use by another connection.

**Related Information**  


[ALTER PROCEDURE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](alter-procedure-statement-for-data-lake-relational-engine-sap-hana-db-managed-96adbf3.md "Replaces an existing procedure with a modified version. Include the entire modified procedure in the ALTER PROCEDURE statement, and reassign user permissions on the procedure.")

[CREATE PROCEDURE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](create-procedure-statement-for-data-lake-relational-engine-sap-hana-db-managed-d172ce3.md "Creates a new user-defined SQL procedure in the database.")

[DROP Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a61c216b84f21015baa181c153419bbb.html "Removes objects from the database.") :arrow_upper_right:

