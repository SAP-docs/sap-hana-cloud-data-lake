<!-- loioa6142def84f2101591f2a40a1dd6cb20 -->

# BEGIN … END Statement for Data Lake Relational Engine

Groups SQL statements together.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
[ <statement-label> : ]
        … BEGIN [ [ NOT ] ATOMIC ]
        … [ <local-declaration> ; … ]
        … <statement-list>
        … [ EXCEPTION [ <exception-case> … ] ]
        … END [ <statement-label> ]
```

```
<local-declaration> ::=
        { <variable-declaration> 
        | <cursor-declaration> 
        | <exception-declaration> 
        | <temporary-table-declaration> }
```

```
<variable-declaration> ::=
        DECLARE <variable-name> [ , … ] <data-type> 
        [{ = | DEFAULT} <initial-value> ]
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
   { CURRENT { DATABASE 
             | DATE 
             | PUBLISHER 
             | TIME 
             | TIMESTAMP 
             | USER 
             | UTC TIMESTAMP } 
   | USER }
```



<a name="loioa6142def84f2101591f2a40a1dd6cb20__begin_end_param1"/>

## Parameters

 *<statement-label\>*
 :   If specified, it must match the beginning *<statement-label\>*. You can use the `LEAVE` statement to resume execution at the first statement after the compound statement. The compound statement that is the body of a procedure has an implicit label that is the same as the name of the procedure.

  *<initial-value\>*
 :   If specified, the variable is set to that value and the data type must match the type defined by *<data-type\>*. If you do not specify an initial-value, the variable contains the NULL value until a `SET` statement assigns a different value.

 

<a name="loioa6142def84f2101591f2a40a1dd6cb20__begin_end_remarks1"/>

## Remarks

The body of a procedure is a compound statement. Compound statements can also be used in control statements within a procedure.

A compound statement allows one or more SQL statements to be grouped together and treated as a unit. A compound statement starts with `BEGIN` and ends with `END`. Immediately after `BEGIN`, a compound statement can have local declarations that exist only within the compound statement. A compound statement can have a local declaration for a variable, a cursor, a temporary table, or an exception. Local declarations can be referenced by any statement in that compound statement, or in any compound statement nested within it. Local declarations are invisible to other procedures that are called from within a compound statement.

An atomic statement is a statement executed completely or not at all. For example, an `UPDATE` statement that updates thousands of rows might encounter an error after updating many rows. If the statement does not complete, all changes revert back to their original state. Similarly, if you specify that the `BEGIN` statement is atomic, the statement is executed either in its entirety or not at all.



<a name="loioa6142def84f2101591f2a40a1dd6cb20__begin_end_privileges1"/>

## Privileges



### 

None



<a name="loioa6142def84f2101591f2a40a1dd6cb20__begin_end_standards1"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – supported by SAP Adaptive Server Enterprise. This does not mean that all statements inside a compound statement are supported.

    `BEGIN` and `END` keywords are not required in Transact-SQL.

    `BEGIN` and `END` are used in Transact-SQL to group a set of statements into a single compound statement, so that control statements such as `IF … ELSE`, which affect the performance of only a single SQL statement, can affect the performance of the whole group. The ATOMIC keyword is not supported by SAP ASE.

    In Transact-SQL, `DECLARE` statements need not immediately follow `BEGIN`, and the cursor or variable that is declared exists for the duration of the compound statement. You should declare variables at the beginning of the compound statement for compatibility.




<a name="loioa6142def84f2101591f2a40a1dd6cb20__begin_end_examples1"/>

## Examples

In the following example, the body of a procedure is a compound statement:

```
CREATE PROCEDURE TopCustomer (OUT TopCompany CHAR(35), OUT TopValue INT)
          BEGIN
          DECLARE err_notfound EXCEPTION FOR
          SQLSTATE '02000' ;
          DECLARE curThisCust CURSOR FOR
          SELECT CompanyName, CAST(
          sum(SalesOrderItems.Quantity *
          Products.UnitPrice) AS INTEGER) VALUE
          FROM Customers
          LEFT OUTER JOIN Salesorders
          LEFT OUTER JOIN SalesOrderItems
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
          END
```

**Related Information**  


[DECLARE CURSOR Statement \[ESQL\] \[SP\] for Data Lake Relational Engine](declare-cursor-statement-esql-sp-for-data-lake-relational-engine-a61ac0b.md "Declares a cursor. Cursors are the primary means for manipulating the results of queries.")

[DECLARE LOCAL TEMPORARY TABLE Statement for Data Lake Relational Engine](declare-local-temporary-table-statement-for-data-lake-relational-engine-a61b247.md "Declares a local temporary table.")

[LEAVE Statement for Data Lake Relational Engine](leave-statement-for-data-lake-relational-engine-a6206e0.md "Continues execution by leaving a compound statement or LOOP.")

[RESIGNAL Statement for Data Lake Relational Engine](resignal-statement-for-data-lake-relational-engine-a6233dc.md "Resignals an exception condition.")

[SIGNAL Statement for Data Lake Relational Engine](signal-statement-for-data-lake-relational-engine-a6266b2.md "Lets you raise an exception condition.")

[BEGIN … END Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/cfaf187bc70744e192136ee62c3b65b6.html "Groups SQL statements together.") :arrow_upper_right:

