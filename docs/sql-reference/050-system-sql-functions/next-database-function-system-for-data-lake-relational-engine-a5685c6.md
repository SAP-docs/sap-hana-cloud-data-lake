<!-- loioa5685c6784f21015954982d535b57bac -->

# NEXT\_DATABASE Function \[System\] for Data Lake Relational Engine

Returns the next database ID number, or the first database if the parameter is NULL.



```
NEXT_DATABASE ( { NULL | <database-id> } )
```



<a name="loioa5685c6784f21015954982d535b57bac__iq_refbb_795"/>

## Parameters

 *<database-id\>*
 :   An integer that specifies the ID number of the database.

 

## Returns

INT



<a name="loioa5685c6784f21015954982d535b57bac__iq_refbb_798"/>

## Remarks

> ### Note:  
> CIS functional compensation performance considerations apply.

You can use NEXT\_DATABASE to enumerate the databases running on a database server. To get the first database, pass NULL. Tto get each subsequent database, pass the previous return value. The function returns NULL when there are no more databases.



<a name="loioa5685c6784f21015954982d535b57bac__iq_refbb_799"/>

## Standards and Compatibility

-   SQL – Transact-SQL extension to ISO/ANSI SQL grammar



<a name="loioa5685c6784f21015954982d535b57bac__iq_refbb_797"/>

## Examples

-   The following statement returns the value 0, the first database value:

    ```
    SELECT NEXT_DATABASE( NULL ) FROM iq_dummy
    ```

-   The following statement returns NULL, indicating that there are no more databases on the server:

    ```
    SELECT NEXT_DATABASE( 0 ) FROM iq_dummy
    ```


**Related Information**  


[DB\_ID Function \[System\] for Data Lake Relational Engine](db-id-function-system-for-data-lake-relational-engine-a54ac47.md "Returns the database ID number.")

[DB\_NAME Function \[System\] for Data Lake Relational Engine](db-name-function-system-for-data-lake-relational-engine-a54b690.md "Returns the database name.")

[DB\_PROPERTY Function \[System\] for Data Lake Relational Engine](db-property-function-system-for-data-lake-relational-engine-a54c05b.md "Returns the value of the given property.")

[OBJECT\_ID Function \[System\] for Data Lake Relational Engine](object-id-function-system-for-data-lake-relational-engine-a56b078.md "Returns the object ID.")

[OBJECT\_NAME Function \[System\] for Data Lake Relational Engine](object-name-function-system-for-data-lake-relational-engine-a56b844.md "Returns the object name.")

