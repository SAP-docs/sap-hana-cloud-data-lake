<!-- loioa638259c84f210159846ce8b3b1237ec -->

# HASH\_THRASHING\_PERCENT Option for Data Lake Relational Engine

Specifies the percent of hard disk I/Os allowed during the execution of a statement that includes a query involving hash algorithms, before the statement is rolled back and an error message is reported.



> ### Restriction:  
> This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa638259c84f210159846ce8b3b1237ec__iq_refso_583"/>

## Default

10



<a name="loioa638259c84f210159846ce8b3b1237ec__iq_refso_585"/>

## Remarks

If a query that uses hash algorithms causes an excessive number of hard disk I/Os \(paging buffers from memory to disk\), query performance is negatively affected, and server performance might also be affected. HASH\_THRASHING\_PERCENT controls the percentage of hard disk I/Os allowed before the statement is rolled back, and you see one of the following error messages:

-   ***Hash insert thrashing detected.***
-   ***Hash find thrashing detected.***

**Related Information**  


[HASH\_PINNABLE\_CACHE\_PERCENT Option for Data Lake Relational Engine](hash-pinnable-cache-percent-option-for-data-lake-relational-engine-a637f5a.md "Controls the maximum percentage of a user’s temp memory that a hash object can pin.")

