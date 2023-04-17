<!-- loioe20777f88e5744e2956812882ed7d661 -->

# Interrow Functions Usage in Data Lake Relational Engine \(SAP HANA DB-Managed\)

The interrow functions LAG and LEAD enable access to previous values or subsequent values in a data series.

These functions provide access to more than one row of a table or partition simultaneously without a self join. The LAG function provides access to a row at a given physical offset prior to the CURRENT ROW in the table or partition. The LEAD function provides access to a row at a given physical offset after the CURRENT ROW in the table or partition. Use the LAG and LEAD functions to create queries such as, "What was the stock price two intervals before the current row?" and "What was the stock price one interval after the current row?"

Interrow functions require an OVER \(ORDER\_BY\) clause.

**Related Information**  


[LAG Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](lag-function-for-data-lake-relational-engine-sap-hana-db-managed-0561e54.md "An interrow function that returns the value of an attribute in a previous row in the table or table partition.")

[LEAD Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](lead-function-for-data-lake-relational-engine-sap-hana-db-managed-b6a23b0.md "An interrow function that returns the value of an attribute in a subsequent row in the table or table partition.")

