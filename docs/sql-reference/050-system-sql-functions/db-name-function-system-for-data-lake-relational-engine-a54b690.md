<!-- loioa54b690484f21015b21ebe23e239b7fb -->

# DB\_NAME Function \[System\] for Data Lake Relational Engine

Returns the database name.



```
DB_NAME ( [ <database-id> ] );
```



<a name="loioa54b690484f21015b21ebe23e239b7fb__iq_refbb_474"/>

## Parameters


<dl>
<dt><b>

*<database-id\>*

</b></dt>
<dd>

The ID of the database, in the form of a numeric expression.



</dd>
</dl>



## Result Set

VARCHAR



<a name="loioa54b690484f21015b21ebe23e239b7fb__iq_refbb_477"/>

## Remarks

> ### Note:  
> CIS functional compensation performance considerations apply.

If no *<database-id\>* is supplied, the name of the current database is returned.



<a name="loioa54b690484f21015b21ebe23e239b7fb__iq_refbb_478"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa54b690484f21015b21ebe23e239b7fb__iq_refbb_476"/>

## Example

Returns the database name iqdemo, when executed against the iq\_dummy database:

```
SELECT DB_NAME( 0 ) FROM iq_dummy;
```

**Related Information**  


[DB\_PROPERTY Function \[System\] for Data Lake Relational Engine](db-property-function-system-for-data-lake-relational-engine-a54c05b.md "Returns the value of the given property.")

[NEXT\_DATABASE Function \[System\] for Data Lake Relational Engine](next-database-function-system-for-data-lake-relational-engine-a5685c6.md "Returns the next database ID number, or the first database if the parameter is NULL.")

[OBJECT\_ID Function \[System\] for Data Lake Relational Engine](object-id-function-system-for-data-lake-relational-engine-a56b078.md "Returns the object ID.")

[OBJECT\_NAME Function \[System\] for Data Lake Relational Engine](object-name-function-system-for-data-lake-relational-engine-a56b844.md "Returns the object name.")

