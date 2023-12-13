<!-- loio96adbf340029431f89eac847e1068eac -->

# ALTER PROCEDURE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Replaces an existing procedure with a modified version. Include the entire modified procedure in the ALTER PROCEDURE statement, and reassign user permissions on the procedure.



## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:

-   Connected to SAP HANA database as a SAP HANA database user and using the SAP HANA database REMOTE\_EXECUTE procedure.
-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
ALTER PROCEDURE [ <schema-name>.]<procedure-name> 
   { <procedure-definition>
   | REPLICATE { ON | OFF }
   | SET HIDDEN
   | RECOMPILE };
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio96adbf340029431f89eac847e1068eac__section_pwz_p5k_sqb"/>

## Parameters


<dl>
<dt><b>

REPLICATE \{ ON | OFF \}

</b></dt>
<dd>

If a procedure needs to be relocated to other sites using SAP Replication Server, use the REPLICATE ON clause.



</dd><dt><b>

SET HIDDEN

</b></dt>
<dd>

To obfuscate the definition of the associated procedure and cause it to become unreadable. The procedure can be unloaded and reloaded into other databases.

> ### Caution:  
> This setting is irreversible. You should retain the original procedure definition outside of the database.



</dd><dt><b>

RECOMPILE

</b></dt>
<dd>

Recompiles a stored procedure. When you recompile a procedure, the definition stored in the catalog is re-parsed and the syntax is verified. The procedure definition is not changed by recompiling. You can recompile procedures with definitions hidden with the SET HIDDEN clause, but their definitions remain hidden.



</dd><dt><b>

RESULT

</b></dt>
<dd>

For procedures that generate a result set, but do not include a RESULT clause, the database server attempts to determine the result set characteristics for the procedure and stores the information in the catalog. This can be useful if a table referenced by the procedure has been altered to add, remove, or rename columns since the procedure was created.



</dd><dt><b>

*<environment-name\>*

</b></dt>
<dd>

DISALLOW is the default. ALLOW indicates that server-side connections are allowed.

> ### Note:  
> -   Do not specify ALLOW unless necessary. Use of the ALLOW clause slows down certain types of data lake Relational Engine table joins.



</dd>
</dl>



<a name="loio96adbf340029431f89eac847e1068eac__section_mgd_r5k_sqb"/>

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



<a name="loio96adbf340029431f89eac847e1068eac__section_gbl_1cq_wwb"/>

## Privileges



### 

The privileges required depend on your data lake Relational Engine \(SAP HANA DB-Managed\) connection method:


<dl>
<dt><b>

Connected to SAP HANA database as a SAP HANA database user and using the SAP HANA database REMOTE\_EXECUTE procedure:

</b></dt>
<dd>

Requires one of:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the SAP HANA database REMOTE\_EXECUTE procedure associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).

-   See [REMOTE\_EXECUTE Guidance and Examples for Executing SQL Statements](remote-execute-guidance-and-examples-for-executing-sql-statements-fd99ac0.md).




</dd><dt><b>

Connected directly to data lake Relational Engine as a data lake Relational Engine user:

</b></dt>
<dd>

Requires one of:

-   You own the Watcom SQL or Transact-SQL procedure.
-   ALTER ANY PROCEDURE system privilege
-   ALTER ANY OBJECT system privilege
-   ALTER object-level privilege on the schema containing the procedure if the schema is owned by another user.

For information on using a procedure created when connected as a data lake Relational Engine user, see [User-Defined Procedures in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2023_4_QRC/en-US/44dbf05fa907437b9145f1541cdbb920.html "User-defined procedures perform one or more specific tasks in data lake Relational Engine.") :arrow_upper_right:.



</dd>
</dl>



<a name="loio96adbf340029431f89eac847e1068eac__section_gt1_t5k_sqb"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP SQL Anywhere

**Related Information**  


[CREATE PROCEDURE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](create-procedure-statement-for-data-lake-relational-engine-sap-hana-db-managed-d172ce3.md "Creates a new user-defined SQL procedure in the database.")

[DROP PROCEDURE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](drop-procedure-statement-for-data-lake-relational-engine-sap-hana-db-managed-86898fa.md "Removes a user-defined procedure from the database.")

[ALTER PROCEDURE Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/a612e25a84f210158dbcdec111da3e96.html "Replaces an existing procedure with a modified version. Include the entire modified procedure in the ALTER PROCEDURE statement, and reassign user permissions on the procedure.") :arrow_upper_right:

