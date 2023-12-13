<!-- loioa61f4dea84f2101596209eca0aa72455 -->

# IF Statement for Data Lake Relational Engine

Lets you conditionally execute the first list of SQL statements whose *<search-condition\>* evaluates to TRUE.



<a name="loioa61f4dea84f2101596209eca0aa72455__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
IF <search-condition> THEN <statement-list>
... [ ELSEIF <search-condition> THEN <statement-list> ]...
... [ ELSE <statement-list> ]
... END IF;
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa61f4dea84f2101596209eca0aa72455__IQ_Usage"/>

## Remarks

If no *<search-condition\>* evaluates to TRUE, and an ELSE clause exists, the *<statement-list\>* in the ELSE clause is executed. If no *<search-condition\>* evaluates to TRUE, and there is no ELSE clause, the expression returns a NULL value.

Execution resumes at the first statement after the END IF.

When comparing variables to the single value returned by a `SELECT` statement inside an `IF` statement, you must first assign the result of the `SELECT` to another variable.

> ### Note:  
> Do not confuse the syntax of the `IF` statement with that of the IF expression. You cannot nest the `IF` statement.



<a name="loioa61f4dea84f2101596209eca0aa72455__IQ_Permissions"/>

## Privileges

None



<a name="loioa61f4dea84f2101596209eca0aa72455__IQ_Standards"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products – the Transact-SQL `IF` statement has a slightly different syntax.



<a name="loioa61f4dea84f2101596209eca0aa72455__IQ_Examples"/>

## Examples

-   The following example illustrates the use of the `IF` statement:

    ```
    CREATE PROCEDURE TopCustomer (OUT TopCompany CHAR(35), OUT TopValue INT)
    BEGIN
    	DECLARE err_notfound EXCEPTION
    	FOR SQLSTATE '02000' ;
    	DECLARE curThisCust CURSOR FOR
    	SELECT CompanyName, CAST( 	sum(SalesOrderItems.Quantity *
    	Products.UnitPrice) AS INTEGER) VALUE
    	FROM Customers
    	LEFT OUTER JOIN SalesOrders
    	LEFT OUTER JOIN SalesOrsderItems
    	LEFT OUTER JOIN Product
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

-   The following example illustrates the use of the `ELSEIF` statement:

    ```
    
    BEGIN
     DECLARE X INT;
     SET X = 1;
     IF X = 1 THEN
      PRINT '1';
      ELSEIF X = 2 THEN
       PRINT '2';
      ELSE
       PRINT 'something else';
     ENDIF
    END
    ;
    ```


**Related Information**  


[BEGIN … END Statement for Data Lake Relational Engine](begin-end-statement-for-data-lake-relational-engine-a6142de.md "Groups SQL statements together.")

