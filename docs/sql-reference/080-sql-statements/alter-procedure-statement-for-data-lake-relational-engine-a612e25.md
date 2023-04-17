<!-- loioa612e25a84f210158dbcdec111da3e96 -->

# ALTER PROCEDURE Statement for Data Lake Relational Engine

Replaces an existing procedure with a modified version. Include the entire modified procedure in the ALTER PROCEDURE statement, and reassign user permissions on the procedure.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
ALTER PROCEDURE [ [/pandoc/div/div/horizontalrule/codeblock/span/span
     {""}) { [/pandoc/div/div/horizontalrule/codeblock/span/span/varname
     {"varname"}) <owner> (varname] | [/pandoc/div/div/horizontalrule/codeblock/span/span/varname
     {"varname"}) <schema-name> (varname] } (span].][/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <procedure-name> (varname] 
   { [/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <procedure-definition> (varname]
   | REPLICATE { ON | OFF }
   | SET HIDDEN
   | RECOMPILE }
```



<a name="loioa612e25a84f210158dbcdec111da3e96__alter_proc_parameters1"/>

## Parameters

 REPLICATE \{ ON | OFF \}
 :   If a procedure needs to be relocated to other sites using SAP Replication Server, use the REPLICATE ON clause.

  SET HIDDEN
 :   To obfuscate the definition of the associated procedure and cause it to become unreadable. The procedure can be unloaded and reloaded into other databases.

    > ### Caution:  
    > This setting is irreversible. You should retain the original procedure definition outside of the database.

  RECOMPILE
 :   Recompiles a stored procedure. When you recompile a procedure, the definition stored in the catalog is re-parsed and the syntax is verified. The procedure definition is not changed by recompiling. You can recompile procedures with definitions hidden with the SET HIDDEN clause, but their definitions remain hidden.

  RESULT
 :   For procedures that generate a result set, but do not include a RESULT clause, the database server attempts to determine the result set characteristics for the procedure and stores the information in the catalog. This can be useful if a table referenced by the procedure has been altered to add, remove, or rename columns since the procedure was created.

  *<environment-name\>*
 :   DISALLOW is the default. ALLOW indicates that server-side connections are allowed.

    > ### Note:  
    > -   Do not specify ALLOW unless necessary. Use of the ALLOW clause slows down certain types of data lake Relational Engine table joins.

 

<a name="loioa612e25a84f210158dbcdec111da3e96__alter_proc_remarks1"/>

## Remarks

The ALTER PROCEDURE statement must include the entire new procedure. You can use PROC as a synonym for PROCEDURE. Both Watcom and Transact-SQL dialect procedures can be altered through the use of ALTER PROCEDURE. Existing permissions on the procedure are not changed. If you execute DROP PROCEDURE followed by CREATE PROCEDURE, execute permissions are reassigned.

You cannot combine Syntax 2 with Syntax 1.

> ### Note:  
> For **required** parameters that accept variable names, an error is returned if one of the following conditions is true:
> 
> -   The variable does not exist
> -   The contents of the variable are NULL
> -   The variable exceeds the length allowed by the parameter
> -   The data type of the variable does not match that required by the parameter



<a name="loioa612e25a84f210158dbcdec111da3e96__alter_proc_priv1"/>

## Privileges



### 

Requires one of:

-   You own the Watcom SQL or Transact-SQL procedure.
-   ALTER ANY PROCEDURE system privilege
-   ALTER ANY OBJECT system privilege
-   ALTER object-level privilege on the schema containing the procedure if the schema is owned by another user.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



<a name="loioa612e25a84f210158dbcdec111da3e96__alter_proc_standards1"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP SQL Anywhere

**Related Information**  


[CREATE PROCEDURE Statement for Data Lake Relational Engine](create-procedure-statement-for-data-lake-relational-engine-a6185b2.md "Creates a new user-defined SQL procedure in the database.")

[DROP Statement for Data Lake Relational Engine](drop-statement-for-data-lake-relational-engine-a61c216.md "Removes objects from the database.")

[ALTER PROCEDURE Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/96adbf340029431f89eac847e1068eac.html "Replaces an existing procedure with a modified version. Include the entire modified procedure in the ALTER PROCEDURE statement, and reassign user permissions on the procedure.") :arrow_upper_right:

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")
