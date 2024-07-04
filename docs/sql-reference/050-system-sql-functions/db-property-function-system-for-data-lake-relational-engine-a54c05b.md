<!-- loioa54c05bf84f210159e15ebbba6819ce4 -->

# DB\_PROPERTY Function \[System\] for Data Lake Relational Engine

Returns the value of the given property.



```
DB_PROPERTY ( { <property-id> | <property-name> }
[ , { <database-id> | <database-name> } ] );
```



<a name="loioa54c05bf84f210159e15ebbba6819ce4__iq_refbb_480"/>

## Parameters


<dl>
<dt><b>

*<property-id\>*

</b></dt>
<dd>

The database property ID.



</dd><dt><b>

*<property-name\>*

</b></dt>
<dd>

The database property name.



</dd><dt><b>

*<database-id\>*

</b></dt>
<dd>

The database ID number, as returned by DB\_ID. Typically, the database name is used.



</dd><dt><b>

*<database-name\>*

</b></dt>
<dd>

The name of the database, as returned by DB\_NAME.



</dd>
</dl>



## Result Set

VARCHAR



<a name="loioa54c05bf84f210159e15ebbba6819ce4__iq_refbb_483"/>

## Remarks

> ### Note:  
> CIS functional compensation performance considerations apply.

Returns a string. The current database is used if the second argument is omitted.



<a name="loioa54c05bf84f210159e15ebbba6819ce4__iq_refbb_484"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa54c05bf84f210159e15ebbba6819ce4__iq_refbb_482"/>

## Examples

The following statement returns the page size of the current database, in bytes:

```
SELECT DB_PROPERTY( 'PAGESIZE' ) FROM iq_dummy;
```

**Related Information**  


[DB\_NAME Function \[System\] for Data Lake Relational Engine](db-name-function-system-for-data-lake-relational-engine-a54b690.md "Returns the database name.")

[NEXT\_DATABASE Function \[System\] for Data Lake Relational Engine](next-database-function-system-for-data-lake-relational-engine-a5685c6.md "Returns the next database ID number, or the first database if the parameter is NULL.")

[OBJECT\_ID Function \[System\] for Data Lake Relational Engine](object-id-function-system-for-data-lake-relational-engine-a56b078.md "Returns the object ID.")

[OBJECT\_NAME Function \[System\] for Data Lake Relational Engine](object-name-function-system-for-data-lake-relational-engine-a56b844.md "Returns the object name.")

