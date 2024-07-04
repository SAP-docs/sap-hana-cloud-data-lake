<!-- loioa618891584f210158ae1b5a5cdce0a34 -->

# CREATE PROCEDURE Statement \[T-SQL\] for Data Lake Relational Engine

Creates a new procedure that is compatible with SAP Adaptive Server Enterprise.



<a name="loioa618891584f210158ae1b5a5cdce0a34__section_azh_5fj_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



This subset of the Transact-SQL CREATE PROCEDURE statement is supported in data lake Relational Engine.



```
CREATE [ OR REPLACE ] PROCEDURE { <owner> | <schema-name> }.]<procedure-name>
   … [ [ ( ] <@parameter_name> <data-type> [ = <default> ] [ OUTPUT ] [ , … ] [ ) ] ]
   … [ WITH RECOMPILE ]
   … AS
   … <statement-list>
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa618891584f210158ae1b5a5cdce0a34__create_tsql_proc_parameters1"/>

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



<a name="loioa618891584f210158ae1b5a5cdce0a34__create_tsql_proc_remarks1"/>

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



<a name="loioa618891584f210158ae1b5a5cdce0a34__create_tsql_proc_privileges1"/>

## Privileges



### 

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



See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



<a name="loioa618891584f210158ae1b5a5cdce0a34__create_tsql_proc_side_effects1"/>

## Side Effects

Automatic commit



<a name="loioa618891584f210158ae1b5a5cdce0a34__creat_tsql_proc_standards1"/>

## Standards

-   SQL – Transact-SQL extension to ISO/ANSI SQL grammar
-   SAP database products – data lake Relational Engine supports a subset of the SAP ASE CREATE PROCEDURE statement syntax.

**Related Information**  


[CREATE PROCEDURE Statement \[T-SQL\] for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/873f31b35574493f8d3a7974681eccb3.html "Creates a new procedure that is compatible with SAP Adaptive Server Enterprise.") :arrow_upper_right:

