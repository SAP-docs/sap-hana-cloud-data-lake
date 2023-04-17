<!-- loioff6ff4190a884a6a8ed71e9ebb1cdba4 -->

# IF Expressions in Data Lake Relational Engine \(SAP HANA DB-Managed\)

The IF expression provides IF-THEN-ELSE SQL expressions.



The syntax of the IF expression is as follows:

```
IF <condition>
THEN <expression1> 
[ ELSE <expression2> ] 
ENDIF
```

This expression returns:

-   If *<condition\>* is TRUE – then the IF expression returns *<expression1\>*.

-   If *<condition\>* is FALSE – then the IF expression returns *<expression2\>*.

-   If *<condition\>* is FALSE – and there is no *<expression2\>*, then the IF expression returns NULL.

-   If *<condition\>* is NULL – then the IF expression returns NULL.


> ### Note:  
> IF statement is different from IF expression.
> 
> Do not confuse the syntax of the IF expression with that of the IF statement.

