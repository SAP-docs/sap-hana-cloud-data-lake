<!-- loioa52da06984f21015bf279b4c69002e5e -->

# System Information in Data Lake Relational Engine

System functions return system information.



<a name="loioa52da06984f21015bf279b4c69002e5e__SYSFUNCS_desc1"/>

## Description

A set of system functions provides information about properties of a currently running database, or of a connection, on the database server. These system functions take the database name or ID, or the connection name, as an optional argument to identify the databaseor connection for which the property is requested.



<a name="loioa52da06984f21015bf279b4c69002e5e__SYSFUNCS_perf1"/>

## Performance

System functions are processed differently than other data lake Relational Engine functions. When queries to data lake Relational Engine tables include system functions, performance is reduced.



The following functions are available:

-   [CONNECTION\_PROPERTY Function \[System\] for Data Lake Relational Engine](../050-system-sql-functions/connection-property-function-system-for-data-lake-relational-engine-a53eeaf.md)
-   [DATALENGTH Function \[System\] for Data Lake Relational Engine](../050-system-sql-functions/datalength-function-system-for-data-lake-relational-engine-a543941.md)
-   [DB\_ID Function \[System\] for Data Lake Relational Engine](../050-system-sql-functions/db-id-function-system-for-data-lake-relational-engine-a54ac47.md)
-   [DB\_NAME Function \[System\] for Data Lake Relational Engine](../050-system-sql-functions/db-name-function-system-for-data-lake-relational-engine-a54b690.md)
-   [DB\_PROPERTY Function \[System\] for Data Lake Relational Engine](../050-system-sql-functions/db-property-function-system-for-data-lake-relational-engine-a54c05b.md)
-   [EVENT\_CONDITION Function \[System\] for Data Lake Relational Engine](../050-system-sql-functions/event-condition-function-system-for-data-lake-relational-engine-a54fb34.md)
-   [EVENT\_CONDITION\_NAME Function \[System\] for Data Lake Relational Engine](../050-system-sql-functions/event-condition-name-function-system-for-data-lake-relational-engine-a550344.md)
-   [EVENT\_PARAMETER Function \[System\] for Data Lake Relational Engine](../050-system-sql-functions/event-parameter-function-system-for-data-lake-relational-engine-a550b30.md)
-   [GROUP\_MEMBER Function \[System\] for Data Lake Relational Engine](../050-system-sql-functions/group-member-function-system-for-data-lake-relational-engine-a554c89.md)
-   [NEXT\_CONNECTION Function \[System\] for Data Lake Relational Engine](../050-system-sql-functions/next-connection-function-system-for-data-lake-relational-engine-a567dab.md)
-   [NEXT\_DATABASE Function \[System\] for Data Lake Relational Engine](../050-system-sql-functions/next-database-function-system-for-data-lake-relational-engine-a5685c6.md)
-   [OBJECT\_ID Function \[System\] for Data Lake Relational Engine](../050-system-sql-functions/object-id-function-system-for-data-lake-relational-engine-a56b078.md)
-   [OBJECT\_NAME Function \[System\] for Data Lake Relational Engine](../050-system-sql-functions/object-name-function-system-for-data-lake-relational-engine-a56b844.md)
-   [PROPERTY Function \[System\] for Data Lake Relational Engine](../050-system-sql-functions/property-function-system-for-data-lake-relational-engine-a56fa4d.md)
-   [PROPERTY\_DESCRIPTION Function \[System\] for Data Lake Relational Engine](../050-system-sql-functions/property-description-function-system-for-data-lake-relational-engine-a57024b.md)
-   [PROPERTY\_IS\_TRACKABLE Function \[System\] for Data Lake Relational Engine](../050-system-sql-functions/property-is-trackable-function-system-for-data-lake-relational-engine-65b794c.md)
-   [PROPERTY\_NAME Function \[System\] for Data Lake Relational Engine](../050-system-sql-functions/property-name-function-system-for-data-lake-relational-engine-a570a7e.md)
-   [PROPERTY\_NUMBER Function \[System\] for Data Lake Relational Engine](../050-system-sql-functions/property-number-function-system-for-data-lake-relational-engine-a57131a.md)
-   [SP\_HAS\_ROLE Function \[System\] for Data Lake Relational Engine](../050-system-sql-functions/sp-has-role-function-system-for-data-lake-relational-engine-a44c032.md)
-   [SUSER\_ID Function \[System\] for Data Lake Relational Engine](../050-system-sql-functions/suser-id-function-system-for-data-lake-relational-engine-a5892d8.md)
-   [SUSER\_NAME Function \[System\] for Data Lake Relational Engine](../050-system-sql-functions/suser-name-function-system-for-data-lake-relational-engine-a589ad8.md)
-   [USER\_ID Function \[System\] for Data Lake Relational Engine](../050-system-sql-functions/user-id-function-system-for-data-lake-relational-engine-a58d3ba.md)
-   [USER\_NAME Function \[System\] for Data Lake Relational Engine](../050-system-sql-functions/user-name-function-system-for-data-lake-relational-engine-a58dbf3.md)

**Related Information**  


[CEIL Function \[Numeric\] for Data Lake Relational Engine](../050-system-sql-functions/ceil-function-numeric-for-data-lake-relational-engine-a53a419.md "Returns the smallest integer greater than or equal to the specified expression.")

