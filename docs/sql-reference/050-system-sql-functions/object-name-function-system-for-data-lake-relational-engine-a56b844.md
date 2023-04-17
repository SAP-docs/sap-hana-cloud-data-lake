<!-- loioa56b844884f21015ba6d84cedfda5d23 -->

# OBJECT\_NAME Function \[System\] for Data Lake Relational Engine

Returns the object name.



```
OBJECT_NAME ( <object-id> [ , <database-id> ] )
```



<a name="loioa56b844884f21015ba6d84cedfda5d23__iq_refbb_827"/>

## Parameters

 *<object-id\>*
 :   The object ID.

  *<database-id\>*
 :   The database ID.

 

<a name="loioa56b844884f21015ba6d84cedfda5d23__iq_refbb_830"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – SAP Adaptive Server Enterprise function implemented for data lake Relational Engine



<a name="loioa56b844884f21015ba6d84cedfda5d23__iq_refbb_829"/>

## Example

The following statement returns the name "customer":

```
SELECT OBJECT_NAME ( 100209 ) FROM iq_dummy
```

**Related Information**  


[String Functions in Data Lake Relational Engine](string-functions-in-data-lake-relational-engine-a52d1d9.md "String functions perform conversion, extraction, or manipulation operations on strings, or return information about strings.")

[DB\_ID Function \[System\] for Data Lake Relational Engine](db-id-function-system-for-data-lake-relational-engine-a54ac47.md "Returns the database ID number.")

[DB\_NAME Function \[System\] for Data Lake Relational Engine](db-name-function-system-for-data-lake-relational-engine-a54b690.md "Returns the database name.")

[DB\_PROPERTY Function \[System\] for Data Lake Relational Engine](db-property-function-system-for-data-lake-relational-engine-a54c05b.md "Returns the value of the given property.")

[NEXT\_DATABASE Function \[System\] for Data Lake Relational Engine](next-database-function-system-for-data-lake-relational-engine-a5685c6.md "Returns the next database ID number, or the first database if the parameter is NULL.")

[OBJECT\_ID Function \[System\] for Data Lake Relational Engine](object-id-function-system-for-data-lake-relational-engine-a56b078.md "Returns the object ID.")

