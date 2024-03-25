<!-- loioa614f1b784f21015881ec813cf926bf0 -->

# CASE Statement for Data Lake Relational Engine

The CASE statement is a control statement that lets you choose a list of SQL statements to execute based on the value of an expression.



<a name="loioa614f1b784f21015881ec813cf926bf0__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
CASE <value-expression>
   … WHEN [ <constant> | NULL ] THEN <statement-list> …
   … [ WHEN [ <constant> | NULL ] THEN <statement-list> ] …
   … ELSE <statement-list>
   … END
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa614f1b784f21015881ec813cf926bf0__IQ_Usage"/>

## Remarks

If a WHEN clause exists for the value of *<value-expression\>*, the *<statement-list\>* in the WHEN clause is executed. If no appropriate WHEN clause exists, and an ELSE clause exists, the *<statement-list\>* in the ELSE clause is executed. Execution resumes at the first statement after the END.

> ### Note:  
> The ANSI standard allows two forms of `CASE` statements. Although data lake Relational Engine allows both forms, when `CASE` is in the predicate, for best performance you must use the form shown here.
> 
> If you require the other form \(also called ANSI syntax\) for compatibility with SAP SQL Anywhere, use this syntax:
> 
> ```
> CASE
>    WHEN [ search-condition | NULL] THEN statement-list ...
>    [ WHEN [ search-condition | NULL] THEN statement-list ] ...
>    [ ELSE statement-list ]
>    END [ CASE ]
> ```
> 
> With this ANSI syntax form, the statements are executed for the first satisfied search-condition in the `CASE` statement. The ELSE clause is executed if none of the *<search-conditions\>* are met. If the expression can be NULL, use the following syntax for the first *<search-condition\>*:
> 
> ```
> WHEN search-condition IS NULL THEN statement-list
> ```
> 
> Do not confuse the syntax of the `CASE` statement with that of the CASE expression.



<a name="loioa614f1b784f21015881ec813cf926bf0__IQ_Permissions"/>

## Privileges

None



<a name="loioa614f1b784f21015881ec813cf926bf0__IQ_Standards"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loioa614f1b784f21015881ec813cf926bf0__IQ_Examples"/>

## Examples

The following example classifies the products listed in the `Products` table of the demo database into one of shirt, hat, shorts, or unknown:

```
CREATE PROCEDURE ProductType (IN product_id INT, OUT type CHAR(10))
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
  END
```

**Related Information**  


[BEGIN … END Statement for Data Lake Relational Engine](begin-end-statement-for-data-lake-relational-engine-a6142de.md "Groups SQL statements together.")

