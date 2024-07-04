<!-- loiod172ce3def5648e299ecb61779eab7da -->

# CREATE PROCEDURE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Creates a new user-defined SQL procedure in the database.



## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:

-   Connected to SAP HANA database as a SAP HANA database user..
-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
CREATE [ OR REPLACE ] [ TEMPORARY ] PROCEDURE [ <schema-name>.]<procedure-name> ( [ <parameter>, …] ) 
   [ SQL SECURITY { INVOKER | DEFINER } ]
   [ RESULT ( <result-column>, …) | NO RESULT SET ]  
   [ ON EXCEPTION RESUME ]
   { <compound statement> | AT <location-string> }
```

```
<parameter> ::=
   { { IN | OUT | INOUT } <parameter-name> <data-type> [ DEFAULT <expression> ] 
   | SQLCODE 
   | SQLSTATE }
```

```
<result-column> ::= <column-name> <data-type>
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loiod172ce3def5648e299ecb61779eab7da__section_klk_xjl_sqb"/>

## Parameters


<dl>
<dt><b>

*<parameter-name\>*

</b></dt>
<dd>

Parameter names must conform to the rules for other database identifiers, such as column names, and must be a valid SQL data type. The keywords have the following meanings:

Parameters can be prefixed by one of the keywords IN, OUT or INOUT. If no keyword is specified, then parameters are INOUT by default. The keywords have the following meanings:

-   IN – an expression that provides a value to the procedure.
-   OUT – a variable that could be given a value by the procedure.
-   INOUT – a variable that provides a value to the procedure, and could be given a new value by the procedure.

Set the data type explicitly, or specify the %TYPE or %ROWTYPE attribute to set the data type to the data type of another object in the database. Use %TYPE to set it to the data type of a column in a table or view. Use %ROWTYPE to set the data type to a composite data type derived from a row in a table or view. However, defining the data type using a %ROWTYPE that is set to a table reference variable \(TABLE REF \(*<table-reference-variable\>*\) %ROWTYPE is not allowed.



</dd><dt><b>

SQLSTATE and SQLCODE

</b></dt>
<dd>

Special parameters that output the SQLSTATE or SQLCODE value when the procedure ends \(they are OUT parameters\). Whether or not a SQLSTATE and SQLCODE parameter is specified, the SQLSTATE and SQLCODE special values can always be checked immediately after a procedure call to test the return status of the procedure.

The SQLSTATE and SQLCODE special values are modified by the next SQL statement. Providing SQLSTATE or SQLCODE as procedure arguments allows the return code to be stored in a variable.



</dd><dt><b>

OR REPLACE

</b></dt>
<dd>

Replaces an existing procedure with the same name. This clause changes the definition of the procedure, but preserves existing permissions.

You cannot use the OR REPLACE clause with temporary procedures. Also, an error is returned if the procedure being replaced is already in use.



</dd><dt><b>

TEMPORARY

</b></dt>
<dd>

The stored procedure is visible only by the connection that created it, and that it is automatically dropped when the connection is dropped. You can also explicitly drop temporary stored procedures. You cannot perform ALTER, GRANT, or REVOKE on them, and, unlike other stored procedures, temporary stored procedures are not recorded in the catalog or transaction log.

Temporary procedures execute with the permissions of their creator \(current user\), or specified owner. You can specify an owner for a temporary procedure when:

-   The temporary procedure is created within a permanent stored procedure
-   The temporary and permanent procedure both have the same owner

To drop the owner of a temporary procedure, drop the temporary procedure first.

You can create and drop temporary stored procedures when you are connected to a read-only database; they cannot be external procedures.

For example, the following temporary procedure drops the table called CustRank, if it exists. For this example, the procedure assumes that the table name is unique and can be referenced by the procedure creator without specifying the table owner:

```
CREATE TEMPORARY PROCEDURE drop_table( IN @TableName char(128) )
BEGIN
	IF EXISTS  ( SELECT 1 FROM SYS.SYSTAB WHERE
	table_name = @TableName ) 
	THEN EXECUTE IMMEDIATE 
	'DROP TABLE "' || @TableName || '"';
	MESSAGE 'Table "' || @TableName || 
	'" dropped' to client;
	END IF;
END;
CALL drop_table( 'CustRank' );
```



</dd><dt><b>

RESULT

</b></dt>
<dd>

Declares the number and type of columns in the result set. The parenthesized list following the RESULT keyword defines the result column names and types. This information is returned by the Embedded SQL DESCRIBE or by ODBC SQLDescribeCol when a CALL statement is being described.

Some procedures can produce more than one result set, depending on how they are executed. For example, this procedure returns two columns under some circumstances, and one in others:

```
CREATE PROCEDURE names( IN formal char(1))
BEGIN
  IF formal = 'n' THEN
    SELECT GivenName 
    FROM Employees
  ELSE
    SELECT Surname,GivenName 
    FROM Employees
  END IF
END;
```

Procedures with variable result sets must be written without a RESULT clause, or in Transact-SQL. Their use is subject to these limitations:

-   Embedded SQL – you must DESCRIBE the procedure call after the cursor for the result set is opened, but before any rows are returned, in order to get the proper shape of result set. The CURSOR *<cursor-name\>* clause on the DESCRIBE statement is required.
-   ODBC, OLE DB, ADO.NET – variable result-set procedures can be used by ODBC applications. The proper description of the result sets is carried out by the driver or provider.
-   Open Client applications – variable result-set procedures can be used by Open Client applications.

If your procedure returns only one result set, use a RESULT clause. The presence of this clause prevents ODBC and Open Client applications from describing the result set again after a cursor is open.

To handle multiple result sets, ODBC must describe the currently executing cursor, not the procedure’s defined result set. Therefore, ODBC does not always describe column names as defined in the RESULT clause of the procedure definition. To avoid this problem, use column aliases in the SELECT statement that generates the result set.



</dd><dt><b>

NO RESULT SET

</b></dt>
<dd>

Declares that this procedure returns no result set. This is useful when an external environment needs to know that a procedure does not return a result set.



</dd><dt><b>

SQL SECURITY

</b></dt>
<dd>

Defines whether the procedure is executed as the INVOKER \(the user who is calling the procedure\), or as the DEFINER \(the user who owns the procedure\). The default is DEFINER.

Extra memory is used when you specify SQL SECURITY INVOKER, because annotation must be done for each user that calls the procedure. Also, name resolution is performed as the invoker as well. Therefore, qualify all object names \(tables, procedures, and so on\) with their appropriate owner. For example, suppose user1 creates this procedure:

```
CREATE PROCEDURE user1.myProcedure()
   RESULT( columnA INT )
   SQL SECURITY INVOKER
   BEGIN
      SELECT columnA FROM table1;
   END;
```

If user2 attempts to run this procedure and a table user2.table1 does not exist, a table lookup error results. Additionally, if a user2.table1 does exist, that table is used instead of the intended user1.table1. To prevent this situation, qualify the table reference in the statement \(user1.table1, instead of just table1\).



</dd><dt><b>

ON EXCEPTION RESUME

</b></dt>
<dd>

The procedure takes an action that depends on the setting of the ON\_TSQL\_ERROR option. If ON\_TSQL\_ERROR option is set to CONDITIONAL \(which is the default\) the execution continues if the next statement handles the error; otherwise, it exits.

Error-handling statements include:

-   IF
-   SELECT @variable
-   CASE
-   LOOP
-   LEAVE
-   CONTINUE
-   CALL
-   EXECUTE
-   SIGNAL
-   RESIGNAL
-   DECLARE
-   SET VARIABLE

Do not use explicit error-handling code with an ON EXCEPTION RESUME clause.

See *ON\_TSQL\_ERROR Option \[TSQL\]*.



</dd><dt><b>

AT *<location-string\>*

</b></dt>
<dd>

Creates a proxy stored procedure on the current database for a remote procedure specified by *<location-string\>*. The AT clause supports the semicolon \(;\) as a field delimiter in *<location-string\>*. If no semicolon is present, a period is the field delimiter. This allows file names and extensions to be used in the database and owner fields.



</dd>
</dl>



<a name="loiod172ce3def5648e299ecb61779eab7da__section_vt2_zjl_sqb"/>

## Remarks

CREATE PROCEDURE creates a procedure in the database. A procedure is invoked with a CALL statement. You can create permanent or temporary \(TEMPORARY\) stored procedures. You can use PROC as a synonym for PROCEDURE.

> ### Note:  
> There are two ways to create stored procedures: ISO/ANSI SQL and T-SQL. BEGIN TRANSACTION, for example, is T-SQL-specific when using CREATE PROCEDURE syntax. Do not mix syntax when creating stored procedures. See *CREATE PROCEDURE Statement \[T-SQL\]*.

When procedures are executed using CALL, not all parameters need to be specified. If a default value is provided in the CREATE PROCEDURE statement, missing parameters are assigned the default values. If an argument is not provided in the CALL statement, and no default is set, an error is given.

Remote procedures can return only up to 254 characters in output variables.

If a remote procedure can return a result set, even if it does not return one in all cases, then the local procedure definition must contain a RESULT clause.

For information on remote servers, see *CREATE SERVER Statement*.



<a name="loiod172ce3def5648e299ecb61779eab7da__section_tc3_vwr_wwb"/>

## Privileges



### 

The privileges required depend on your data lake Relational Engine \(SAP HANA DB-Managed\) connection method:


<dl>
<dt><b>

Connected to SAP HANA database as a SAP HANA database user.:

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



For information on using a procedure created when connected as a data lake Relational Engine user, see [User-Defined Procedures in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2024_3_QRC/en-US/44dbf05fa907437b9145f1541cdbb920.html "User-defined procedures perform one or more specific tasks in data lake Relational Engine.") :arrow_upper_right:.



</dd>
</dl>



<a name="loiod172ce3def5648e299ecb61779eab7da__section_arr_ckl_sqb"/>

## Side Effects

Automatic commit



<a name="loiod172ce3def5648e299ecb61779eab7da__section_jyv_dkl_sqb"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products – the Transact-SQL CREATE PROCEDURE statement is different.
-   SQLJ – the syntax extensions for Java result sets are as specified in the proposed SQLJ1 standard.



<a name="loiod172ce3def5648e299ecb61779eab7da__section_lfr_fkl_sqb"/>

## Examples

-   The following example uses a case statement to classify the results of a query:

    ```
    CREATE OR REPLACE PROCEDURE ProductType (IN product_id INT, OUT type CHAR(10))
    BEGIN
      DECLARE prod_name CHAR(20) ;
      SELECT name INTO prod_name FROM "GROUPO"."Products"
      WHERE ID = product_id;
      CASE prod_name
      WHEN 'Tee Shirt' THEN
        SET type = 'Shirt'
      WHEN 'Sweatshirt' THEN
        SET type = 'Shirt'
      WHEN 'Baseball Cap' THEN
        SET type = 'Hat'
      WHEN 'Visor' THEN
        SET type = 'Hat'
      WHEN 'Shorts' THEN
        SET type = 'Shorts'
      ELSE
        SET type = 'UNKNOWN'
      END CASE ;
    END;
    ```

-   The following example uses a cursor and loop over the rows of the cursor to return a single value:

    ```
    CREATE PROCEDURE TopCustomer (OUT TopCompany CHAR(35), OUT TopValue INT)
    BEGIN
      DECLARE err_notfound EXCEPTION
     	FOR SQLSTATE '02000' ;
      DECLARE curThisCust CURSOR FOR
      SELECT CompanyName, CAST(   sum(SalesOrderItems.Quantity *
      Products.UnitPrice) AS INTEGER) VALUE
      FROM Customers
      LEFT OUTER JOIN SalesOrders
      LEFT OUTER JOIN SalesorderItems
      LEFT OUTER JOIN Products
      GROUP BY CompanyName ;
    
    
      DECLARE ThisValue INT ;
      DECLARE ThisCompany CHAR(35) ;
      SET TopValue = 0 ;
      OPEN curThisCust ;
      CustomerLoop:
      LOOP
        FETCH NEXT curThisCust
        INTO ThisCompany, ThisValue ;
        IF SQLSTATE = err_notfound THEN
          LEAVE CustomerLoop ;
        END IF ;
        IF ThisValue > TopValue THEN
          SET TopValue = ThisValue ;
          SET TopCompany = ThisCompany ;
          END IF ;
      END LOOP CustomerLoop ;
      CLOSE curThisCust ;
    END;
    ```


**Related Information**  


[ALTER PROCEDURE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](alter-procedure-statement-for-data-lake-relational-engine-sap-hana-db-managed-96adbf3.md "Replaces an existing procedure with a modified version. Include the entire modified procedure in the ALTER PROCEDURE statement, and reassign user permissions on the procedure.")

[DROP PROCEDURE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](drop-procedure-statement-for-data-lake-relational-engine-sap-hana-db-managed-86898fa.md "Removes a user-defined procedure from the database.")

[CREATE PROCEDURE Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a6185b2184f21015b2419a5444b55609.html "Creates a new user-defined SQL procedure in the database.") :arrow_upper_right:

