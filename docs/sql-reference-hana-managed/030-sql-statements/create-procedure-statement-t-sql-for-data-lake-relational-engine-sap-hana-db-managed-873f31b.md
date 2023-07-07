<!-- loio873f31b35574493f8d3a7974681eccb3 -->

# CREATE PROCEDURE Statement \[T-SQL\] for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Creates a new procedure that is compatible with SAP Adaptive Server Enterprise.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Executing SQL Statements](remote-execute-usage-examples-for-executing-sql-statements-fd99ac0.md).
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



This subset of the Transact-SQL `CREATE PROCEDURE` statement is supported in data lake Relational Engine.



```
CREATE [ OR REPLACE ] PROCEDURE <schema-name>.]<procedure-name>
   … [ [ ( ] <@parameter_name> <data-type> [ = <default> ] [ OUTPUT ] [ , … ] [ ) ] ]
   … [ WITH RECOMPILE ]
   … AS
   … <statement-list>
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio873f31b35574493f8d3a7974681eccb3__section_hfk_fhb_5qb"/>

## Parameters


<dl>
<dt><b>

CREATE

</b></dt>
<dd>

Creates a new procedure.



</dd><dt><b>

OR REPLACE

</b></dt>
<dd>

Replaces an existing procedure with the same name. This clause changes the definition of the procedure, but preserves existing permissions.



</dd>
</dl>



<a name="loio873f31b35574493f8d3a7974681eccb3__section_g55_hhb_5qb"/>

## Remarks

Differences between Transact-SQL and data lake Relational Engine SQL statements:

-   Variable names prefixed by @ – the “@” sign denotes a Transact-SQL variable name; data lake Relational Engine variables can be any valid identifier and the @ prefix is optional.

-   Input and output parameters – data lake Relational Engine procedure parameters are specified as IN, OUT, or INOUT; Transact-SQL procedure parameters are INPUT parameters by default or can be specified as OUTPUT. Those parameters declared as INOUT or as OUT in data lake Relational Engine should be declared with OUTPUT in Transact-SQL.

-   Parameter default values – data lake Relational Engine procedure parameters are given a default value using the keyword DEFAULT; Transact-SQL uses an equality sign \(=\) to provide the default value.

-   Returning result sets – data lake Relational Engine uses a RESULT clause to specify returned result sets. In Transact-SQL procedures, the column names or alias names of the first query are returned to the calling environment:

    ```
    CREATE PROCEDURE showdept @deptname varchar(30)
    AS
      SELECT Employees.Surname, Employees.givenName
      FROM Departments, Employees
      WHERE Departments.DepartmentName = @deptname
      AND Departments.DepartmentID =
            Employees.DepartmentID;
    ```

    The corresponding data lake Relational Engine procedure:

    ```
    CREATE PROCEDURE showdept(in deptname 
          varchar(30) )
    RESULT ( lastname char(20), firstname char(20))
    ON EXCEPTION RESUME
    BEGIN
      SELECT Employees.SurName, Employees.GivenName
      FROM Departments, Employees
      WHERE Departments.DepartmentName = deptname
      AND Departments.DepartmentID =
            Employees.DepartmentID
    END;
    ```

-   Procedure body – the body of a Transact-SQL procedure is a list of Transact-SQL statements prefixed by the AS keyword. The body of a data lake Relational Engine procedure is a compound statement, bracketed by BEGIN and END keywords.

    > ### Note:  
    > There are two ways to create stored procedures: T-SQL and SQL/92. BEGIN TRANSACTION, for example, is T-SQL specific when using CREATE PROCEDURE syntax. Do not mix syntax when creating stored procedures.


If the Transact-SQL WITH RECOMPILE optional clause is supplied, it is ignored. SAP SQL Anywhere always recompiles procedures the first time they are executed after a database is started, and stores the compiled procedure until the database is stopped.

Groups of procedures are not supported.



<a name="loio873f31b35574493f8d3a7974681eccb3__section_adf_gcs_wwb"/>

## Privileges



### 

The privileges required depend on your data lake Relational Engine \(SAP HANA DB-Managed\) connection method:


<dl>
<dt><b>

Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure:

</b></dt>
<dd>

Requires one of:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



</dd><dt><b>

Connected directly to data lake Relational Engine as a data lake Relational Engine user:

</b></dt>
<dd>

Requires one of:

-   To create a self owned procedures requires the CREATE PROCEDURE system privilege.
-   To create a procedure owned by another user requires one of:
    -   CREATE ANY PROCEDURE system privilege
    -   CREATE ANY OBJECT system privilege
    -   CREATE ANY object-level privilege on the schema containing the procedure if the schema is owned by another user.

-   To replace an existing procedure requires one of:
    -   You own the procedure.
    -   DROP ANY PROCEURE or DROP ANY OBJECT system privilege along with CREATE ANY PROCEDURE or CREATE ANY OBJECT system privilege
    -   If the procedure is in a schema owned by another user, then you need one of:
        -   DROP and CREATE ANY object-level privilege on the schema
        -   ALTER object-level privilege on the schema.



For information on using a procedure that is created when connected as a data lake Relational Engine user, see [User-Defined Procedures in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2023_1_QRC/en-US/44dbf05fa907437b9145f1541cdbb920.html "User-defined procedures perform one or more specific tasks in data lake Relational Engine.") :arrow_upper_right:.



</dd>
</dl>



<a name="loio873f31b35574493f8d3a7974681eccb3__section_e5z_mhb_5qb"/>

## Side Effects

Automatic commit



<a name="loio873f31b35574493f8d3a7974681eccb3__section_z44_4hb_5qb"/>

## Standards

-   SQL – Transact-SQL extension to ISO/ANSI SQL grammar
-   SAP database products – data lake Relational Engine supports a subset of the SAP ASE CREATE PROCEDURE statement syntax.

**Related Information**  


[CREATE PROCEDURE Statement [T-SQL] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a618891584f210158ae1b5a5cdce0a34.html "Creates a new procedure that is compatible with SAP Adaptive Server Enterprise.") :arrow_upper_right:

