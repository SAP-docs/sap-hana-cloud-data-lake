<!-- loio207a909ff8d84cbab98002e9c653885a -->

# LAG and LEAD Interrow Functions in Data Lake Relational Engine \(SAP HANA DB-Managed\)

The interrow functions, LAG and LEAD, provide access to previous or subsequent values in a data series, or to multiple rows in a table.



Interrow functions also partition simultaneously without a self-join. LAG provides access to a row at a given physical offset before the CURRENT ROW in the table or partition. LEAD provides access to a row at a given physical offset after the CURRENT ROW in the table or partition.

The syntax for LAG and LEAD is identical. Both functions require an OVER \(ORDER\_BY\) window specification.

-   LAG syntax:

    ```
    LAG ( <value_expr> [, <offset> [, <default> ] ] )
         OVER ([PARTITION BY <window partition>] ORDER BY <window ordering>);
    ```

-   LEAD syntax:

    ```
    LEAD (<value_expr>) [, <offset> [, <default>] ] )
        OVER ([PARTITION BY <window partition>] ORDER BY <window ordering>);
    ```


The PARTITION BY clause in the OVER \(ORDER\_BY\) clause is optional. The OVER \(ORDER\_BY\) clause can’t contain a window frame ROWS/RANGE specification.

*<value\_expr\>* is a table column or expression that defines the offset data to return from the table. You can define other functions in the *<value\_expr\>*, except for analytic functions.

For both functions, specify the target row by entering a physical offset. The *<offset\>* value is the number of rows above or below the current row. Enter a non-negative numeric data type \(entering a negative value generates an error\). If you enter 0, data lake Relational Engine returns the current row.

The optional *<default\>* value defines the value to return if the *<offset\>* value goes beyond the scope of the table. The default value of *<default\>* is NULL. The data type of *<default\>* must be implicitly convertible to the data type of the *<value\_expr\>* value, or data lake Relational Engine generates a conversion error.

The interrow functions are useful in financial services applications that perform calculations on data streams, such as stock transactions. The following example uses the LAG function to calculate the percentage change in the trading price of a particular stock. Consider the following trading data from a fictional table called `stock_trades`:

```

TRADED AT            SYMBOL    PRICE
-------------------  ------   ------
2009-07-13 06:07:12  SQL      15.84
2009-07-13 06:07:13  TST       5.75
2009-07-13 06:07:14  TST       5.80
2009-07-13 06:07:15  SQL      15.86
2009-07-13 06:07:16  TST       5.90
2009-07-13 06:07:17  SQL      15.86
```

The query partitions the trades by stock symbol, orders them by time of trade, and uses the LAG function to calculate the percentage increase or decrease in trade price between the current trade and the previous trade:

```
SELECT  STOCK_SYMBOL AS 'Stock',
   traded_at    AS 'Date/Time of Trade',
   trade_price  AS 'Price/Share',
   CAST ( ( ( (TRADE_PRICE
      - (LAG(TRADE_PRICE, 1) 
      OVER (PARTITION BY STOCK_SYMBOL
         ORDER BY TRADED_AT)))
      / TRADE_PRICE)
   * 100.0) AS NUMERIC(5, 2) )
      AS '% Price Change vs Previous Price'
FROM STOCK_TRADES
ORDER BY 1, 2;
```

The query returns these results:

```

Stock   Date/Time of Trade   Price/  % Price Change_vs
symbol                       Share   Previous Price
------  -------------------  -----   -----------------
SQL     2009-07-13 06:07:12  15.84   NULL
SQL     2009-07-13 06:07:15  15.86   0.13
SQL     2009-07-13 06:07:17  15.86   0.00
TST     2009-07-13 06:07:13   5.75   NULL
TST     2009-07-13 06:07:14   5.80   0.87
TST     2009-07-13 06:07:16   5.90   1.72
```

The NULL result in the first and fourth output rows indicates that the LAG function is out of scope for the first row in each of the two partitions. Since there’s no previous row to compare to, data lake Relational Engine returns `NULL` as specified by the *<default\>* variable.

**Related Information**  


[LAG Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](lag-function-for-data-lake-relational-engine-sap-hana-db-managed-0561e54.md "An interrow function that returns the value of an attribute in a previous row in the table or table partition.")

[LEAD Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](lead-function-for-data-lake-relational-engine-sap-hana-db-managed-b6a23b0.md "An interrow function that returns the value of an attribute in a subsequent row in the table or table partition.")

