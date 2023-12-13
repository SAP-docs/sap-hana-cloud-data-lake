<!-- loioa62903f784f2101580008b8c6fbdb47c -->

# WHILE Statement \[T-SQL\] for Data Lake Relational Engine

Provides repeated execution of a statement or compound statement.



<a name="loioa62903f784f2101580008b8c6fbdb47c__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
WHILE <expression>
   ... <statement>;
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa62903f784f2101580008b8c6fbdb47c__IQ_Usage"/>

## Remarks

The `WHILE` conditional affects the performance of only a single SQL statement, unless statements are grouped into a compound statement between the keywords `BEGIN` and `END`.

The `BREAK` statement and `CONTINUE` statement can be used to control execution of the statements in the compound statement. The `BREAK` statement terminates the loop, and execution resumes after the `END` keyword, marking the end of the loop. The `CONTINUE` statement causes the `WHILE` loop to restart, skipping any statements after the `CONTINUE`.



<a name="loioa62903f784f2101580008b8c6fbdb47c__IQ_Permissions"/>

## Privileges

None



<a name="loioa62903f784f2101580008b8c6fbdb47c__IQ_Standards"/>

## Standards

-   SQL – Transact-SQL extension to ISO/ANSI SQL grammar
-   SAP database products – supported by SAP Adaptive Server Enterprise



<a name="loioa62903f784f2101580008b8c6fbdb47c__IQ_Examples"/>

## Examples

The following example shows a `BREAK` statement that breaks the `WHILE` loop, if the most expensive product has a price less than $50. Otherwise, the loop continues until the average price is greater than $30:

```
WHILE (SELECT AVG(unit_price) FROM Products) < 30 
BEGIN
	DELETE FROM Products
	WHERE UnitPrice = MAX(UnitPrice)
	IF ( SELECT MAX(UnitPrice) FROM Products ) < 50 
		BREAK
END;
```

**Related Information**  


[BEGIN … END Statement for Data Lake Relational Engine](begin-end-statement-for-data-lake-relational-engine-a6142de.md "Groups SQL statements together.")

