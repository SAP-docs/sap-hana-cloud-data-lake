<!-- loioa61a929684f210159132aa8321341448 -->

# DECLARE Statement for Data Lake Relational Engine

Declares a SQL variable within a compound statement `(BEGIN... END)`.



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
DECLARE 
   <variable_name>  [ , … ] 
   <data-type> 
   [ { = | DEFAULT } <initial-value>]
```

```
<initial-value> ::=
   { <special-value> 
   | <string> 
   | [ - ] <number> 
   | ( <constant-expression> ) 
   | <built-in-function> ( <constant-expression> ) 
   | NULL }
```

```
<special-value> ::=
   { CURRENT 
     { DATABASE 
      | DATE 
      | PUBLISHER 
      | TIME 
      | TIMESTAMP 
      | USER 
      | UTC TIMESTAMP } 
   | USER }
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa61a929684f210159132aa8321341448__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

*<initial-value\>*

</b></dt>
<dd>

*<data-type\>*. If you do not specify an `initial-value`, the variable contains the NULL value until a `SET` statement assigns a different value.



</dd><dt><b>

*<data-type\>*

</b></dt>
<dd>

Set the data type explicitly, or you can set it by using the %TYPE or %ROWTYPE attribute. Use %TYPE to set it to the data type of a variable or a column in a table or view. Use %ROWTYPE to set the data type to a composite data type derived from a row in a cursor, table, or view.



</dd>
</dl>



<a name="loioa61a929684f210159132aa8321341448__IQ_Usage"/>

## Remarks

Use the `DECLARE` statement to declare variables used in the body of a procedure. The variable persists for the duration of the compound statement in which it is declared and must be unique within the compound statement.

The body of a procedure is a compound statement, and variables must be declared immediately following The variable is set to that value. The data type must match the type defined by `BEGIN`. In a Transact-SQL procedure or trigger, there is no such restriction.



<a name="loioa61a929684f210159132aa8321341448__IQ_Permissions"/>

## Privileges

None



<a name="loioa61a929684f210159132aa8321341448__IQ_Standards"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products – compatible with SAP Adaptive Server Enterprise.
    -   To be compatible with SAP ASE, the variable name must be preceded by an @.
    -   In SAP ASE, a variable that is declared in a procedure or trigger exists for the duration of the procedure or trigger. In data lake Relational EngineThe variable is set to that value. The data type must match the type defined by, if a variable is declared inside a compound statement, it exists only for the duration of that compound statement \(whether it is declared in a data lake Relational Engine SQL or Transact-SQL compound statement\).




<a name="loioa61a929684f210159132aa8321341448__IQ_Examples"/>

## Examples

The following example illustrates the use of the `DECLARE` statement and prints a message on the server window:

```
BEGIN
  DECLARE varname CHAR(61);
  SET varname = 'Test name';
  MESSAGE varname;
END
```

**Related Information**  


[BEGIN … END Statement for Data Lake Relational Engine](begin-end-statement-for-data-lake-relational-engine-a6142de.md "Groups SQL statements together.")

