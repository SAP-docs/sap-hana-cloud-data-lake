<!-- loioa6157e8484f210158041be34e1bf281e -->

# CLOSE Statement \[ESQL\] \[SP\] for Data Lake Relational Engine

Closes a named cursor.



<a name="loioa6157e8484f210158041be34e1bf281e__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
CLOSE { <identifier> | <host-variable> };
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa6157e8484f210158041be34e1bf281e__section_i3v_4j1_ccb"/>

## Remarks

This statement closes the named cursor.

The cursor must have been previously opened.



<a name="loioa6157e8484f210158041be34e1bf281e__IQ_Permissions"/>

## Privileges

None



<a name="loioa6157e8484f210158041be34e1bf281e__IQ_Standards"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – supported by SAP Adaptive Server Enterprise



<a name="loioa6157e8484f210158041be34e1bf281e__IQ_Examples"/>

## Examples

-   The following example closes cursors in Embedded SQL:

    ```
    EXEC SQL CLOSE employee_cursor;
    EXEC SQL CLOSE :cursor_var;
    ```

-   The following example uses a cursor:

    ```
    CREATE PROCEDURE TopCustomer (OUT TopCompany CHAR(35), OUT TopValue INT)
    BEGIN
      DECLARE err_notfound EXCEPTION
      FOR SQLSTATE '02000' ;
      DECLARE curThisCust CURSOR FOR
        SELECT CompanyName, 
          CAST( 	  sum(SalesOrderItems.Quantity *
          Products.UnitPrice) AS INTEGER) VALUE
        FROM Customers
        LEFT OUTER JOIN SalesOrders
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

[OPEN Statement \[ESQL\] \[SP\] for Data Lake Relational Engine](open-statement-esql-sp-for-data-lake-relational-engine-a6215ad.md "Opens a previously declared cursor to access information from the database.")

[PREPARE Statement \[ESQL\] for Data Lake Relational Engine](prepare-statement-esql-for-data-lake-relational-engine-a621eea.md "Prepares a statement to be executed later or used for a cursor.")

