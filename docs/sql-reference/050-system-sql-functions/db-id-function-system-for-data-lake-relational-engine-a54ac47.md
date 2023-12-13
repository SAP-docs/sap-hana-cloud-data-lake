<!-- loioa54ac47c84f2101591f3cf37067c4ad5 -->

# DB\_ID Function \[System\] for Data Lake Relational Engine

Returns the database ID number.



```
DB_ID ( [ <database-name> ] );
```



<a name="loioa54ac47c84f2101591f3cf37067c4ad5__iq_refbb_469"/>

## Parameters


<dl>
<dt><b>

*<database-name\>*

</b></dt>
<dd>

A string expression containing the database name. If database-name is a string constant, it must be enclosed in quotes. If no database-name is supplied, the ID number of the current database is returned.



</dd>
</dl>



## Result Set

INT



<a name="loioa54ac47c84f2101591f3cf37067c4ad5__section_mbl_mkw_x1b"/>

## Remarks

> ### Note:  
> CIS functional compensation performance considerations apply.



<a name="loioa54ac47c84f2101591f3cf37067c4ad5__iq_refbb_472"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa54ac47c84f2101591f3cf37067c4ad5__iq_refbb_471"/>

## Examples

-   Returns the value 0, if `iqdemo` is the only running database:

    ```
    SELECT DB_ID( 'iqdemo' ) FROM iq_dummy;
    ```

-   Returns the value 0, if executed against the only running database:

    ```
    SELECT DB_ID() FROM iq_dummy;
    ```


**Related Information**  


[DB\_NAME Function \[System\] for Data Lake Relational Engine](db-name-function-system-for-data-lake-relational-engine-a54b690.md "Returns the database name.")

[DB\_PROPERTY Function \[System\] for Data Lake Relational Engine](db-property-function-system-for-data-lake-relational-engine-a54c05b.md "Returns the value of the given property.")

[NEXT\_DATABASE Function \[System\] for Data Lake Relational Engine](next-database-function-system-for-data-lake-relational-engine-a5685c6.md "Returns the next database ID number, or the first database if the parameter is NULL.")

[OBJECT\_ID Function \[System\] for Data Lake Relational Engine](object-id-function-system-for-data-lake-relational-engine-a56b078.md "Returns the object ID.")

[OBJECT\_NAME Function \[System\] for Data Lake Relational Engine](object-name-function-system-for-data-lake-relational-engine-a56b844.md "Returns the object name.")

