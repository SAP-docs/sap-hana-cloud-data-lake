<!-- loioa7746d7384f21015ac85eb5019166b85 -->

# EXECUTE Statement \[T-SQL\] for Data Lake Relational Engine

Invokes a procedure, as an SAP Adaptive Server Enterprise-compatible alternative to the `CALL` statement.



<a name="loioa7746d7384f21015ac85eb5019166b85__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
EXECUTE [ <@return_status> = ] [<owner>.]<procedure_name>
   ... { [ <@parameter-name> = ] <expression>
       | [ <@parameter-name> = ] <@variable> [ <output> ] } ,...
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa7746d7384f21015ac85eb5019166b85__IQ_Usage"/>

## Remarks

EXECUTE is implemented for Transact-SQL compatibility, but can be used in either Transact-SQL or executes a stored procedure, optionally supplying procedure parameters and retrieving output values and return status information.data lake Relational Engine batches and procedures.



<a name="loioa7746d7384f21015ac85eb5019166b85__IQ_Permissions"/>

## Privileges

Requires one of:

-   You own the procedure
-   You own the schema containing the procedure
-   EXECUTE ANY PROCEDURE system privilege
-   EXECUTE object-level privilege on the procedure
-   EXECUTE PROCEDURE object-level privilege on the schema that contains the procedure

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) or [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md) for assistance with granting privileges.



<a name="loioa7746d7384f21015ac85eb5019166b85__IQ_Examples"/>

## Examples

Executes a stored procedure, optionally supplying procedure. The following example creates the procedure `p1`:

```
CREATE PROCEDURE p1( @var INTEGER = 54 )
AS
PRINT 'on input @var = %1! ', @var
DECLARE @intvar integer
SELECT @intvar=123
SELECT @var=@intvar
PRINT 'on exit @var = %1!', @var;
```

Execute the procedure, supplying the input value of 23 for the parameter. If you are connected from an Open Client application, `PRINT` messages are displayed on the client window. If you are connected from an ODBC or Embedded SQL application, messages display on the database server window:

```
EXECUTE p1 23;
```

An alternative way of executing the procedure, which is useful if there are several parameters:

```
EXECUTE p1 @var = 23;
```

Execute the procedure, using the default value for the parameter:

```
EXECUTE p1;
```

Execute the procedure and store the return value in a variable for checking return status:

```
EXECUTE @status = p1 23;
```

**Related Information**  


[CALL Statement for Data Lake Relational Engine](call-statement-for-data-lake-relational-engine-a614c16.md "Invokes a procedure.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[REVOKE Object-Level Privilege Statement for Data Lake Relational Engine](revoke-object-level-privilege-statement-for-data-lake-relational-engine-a3e7af2.md "Removes object-level privileges that were given using the GRANT statement.")

