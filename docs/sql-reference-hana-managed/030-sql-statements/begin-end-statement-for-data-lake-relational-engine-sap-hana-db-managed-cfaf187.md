<!-- loiocfaf187bc70744e192136ee62c3b65b6 -->

# BEGIN … END Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Groups SQL statements together.



<a name="loiocfaf187bc70744e192136ee62c3b65b6__section_ahh_bpq_wwb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:

-   Connected to SAP HANA database as a SAP HANA database user..



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



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loiocfaf187bc70744e192136ee62c3b65b6__section_ucc_dpq_wwb"/>

## Parameters


<dl>
<dt><b>

*<statement-label\>*

</b></dt>
<dd>

If specified, it must match the beginning *<statement-label\>*. You can use the `LEAVE` statement to resume execution at the first statement after the compound statement. The compound statement that is the body of a procedure has an implicit label that is the same as the name of the procedure.



</dd><dt><b>

*<initial-value\>*

</b></dt>
<dd>

If specified, the variable is set to that value and the data type must match the type defined by *<data-type\>*. If you do not specify an initial-value, the variable contains the NULL value until a `SET` statement assigns a different value.



</dd>
</dl>



<a name="loiocfaf187bc70744e192136ee62c3b65b6__section_uc1_2pq_wwb"/>

## Remarks

The body of a procedure is a compound statement. Compound statements can also be used in control statements within a procedure.

A compound statement allows one or more SQL statements to be grouped together and treated as a unit. A compound statement starts with `BEGIN` and ends with `END`. Immediately after `BEGIN`, a compound statement can have local declarations that exist only within the compound statement. A compound statement can have a local declaration for a variable, a cursor, a temporary table, or an exception. Local declarations can be referenced by any statement in that compound statement, or in any compound statement nested within it. Local declarations are invisible to other procedures that are called from within a compound statement.

An atomic statement is a statement executed completely or not at all. For example, an `UPDATE` statement that updates thousands of rows might encounter an error after updating many rows. If the statement does not complete, all changes revert back to their original state. Similarly, if you specify that the `BEGIN` statement is atomic, the statement is executed either in its entirety or not at all.



<a name="loiocfaf187bc70744e192136ee62c3b65b6__section_u1g_fpq_wwb"/>

## Privileges



### 


<dl>
<dt><b>

Connected to SAP HANA database as a SAP HANA database user.:

</b></dt>
<dd>

Requires one of:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the SAP HANA database REMOTE\_EXECUTE procedure associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).

-   See [REMOTE\_EXECUTE Guidance and Examples for Executing SQL Statements](remote-execute-guidance-and-examples-for-executing-sql-statements-fd99ac0.md).




</dd>
</dl>



<a name="loiocfaf187bc70744e192136ee62c3b65b6__section_r15_vpq_wwb"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – supported by SAP Adaptive Server Enterprise. This does not mean that all statements inside a compound statement are supported.

    `BEGIN` and `END` keywords are not required in Transact-SQL.

    `BEGIN` and `END` are used in Transact-SQL to group a set of statements into a single compound statement, so that control statements such as `IF … ELSE`, which affect the performance of only a single SQL statement, can affect the performance of the whole group. The ATOMIC keyword is not supported by SAP ASE.

    In Transact-SQL, `DECLARE` statements need not immediately follow `BEGIN`, and the cursor or variable that is declared exists for the duration of the compound statement. You should declare variables at the beginning of the compound statement for compatibility.




<a name="loiocfaf187bc70744e192136ee62c3b65b6__section_twf_ypq_wwb"/>

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


[BEGIN … END Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a6142def84f2101591f2a40a1dd6cb20.html "Groups SQL statements together.") :arrow_upper_right:

