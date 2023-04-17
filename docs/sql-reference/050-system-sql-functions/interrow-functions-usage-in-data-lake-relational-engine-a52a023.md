<!-- loioa52a023284f21015a98f9ec7733f1231 -->

# Interrow Functions Usage in Data Lake Relational Engine

The interrow functions LAG and LEAD enable access to previous values or subsequent values in a data series.

These functions provide access to more than one row of a table or partition simultaneously without a self join. The LAG function provides access to a row at a given physical offset prior to the CURRENT ROW in the table or partition. The LEAD function provides access to a row at a given physical offset after the CURRENT ROW in the table or partition. Use the LAG and LEAD functions to create queries such as, "What was the stock price two intervals before the current row?" and "What was the stock price one interval after the current row?"

Interrow functions require an OVER \(ORDER\_BY\) clause.

**Related Information**  


[LAG Function \[Analytical\] for Data Lake Relational Engine](lag-function-analytical-for-data-lake-relational-engine-a55b772.md "An interrow function that returns the value of an attribute in a previous row in the table or table partition.")

[LEAD Function \[Analytical\] for Data Lake Relational Engine](lead-function-analytical-for-data-lake-relational-engine-a55d051.md "An interrow function that returns the value of an attribute in a subsequent row in the table or table partition.")

