<!-- loioa56b078284f210158dec9fd05131e60d -->

# OBJECT\_ID Function \[System\] for Data Lake Relational Engine

Returns the object ID.



```
OBJECT_ID ( <object-name> );
```



<a name="loioa56b078284f210158dec9fd05131e60d__iq_refbb_822"/>

## Parameters


<dl>
<dt><b>

*<object-name\>*

</b></dt>
<dd>

The name of the object.



</dd>
</dl>



<a name="loioa56b078284f210158dec9fd05131e60d__iq_refbb_825"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – SAP Adaptive Server Enterprise function implemented for data lake Relational Engine



<a name="loioa56b078284f210158dec9fd05131e60d__iq_refbb_824"/>

## Examples

The following statement returns the object ID 100209 of the *<Customers\>* table:

```
SELECT OBJECT_ID ('CUSTOMERS') FROM iq_dummy;
```

**Related Information**  


[DB\_ID Function \[System\] for Data Lake Relational Engine](db-id-function-system-for-data-lake-relational-engine-a54ac47.md "Returns the database ID number.")

[DB\_NAME Function \[System\] for Data Lake Relational Engine](db-name-function-system-for-data-lake-relational-engine-a54b690.md "Returns the database name.")

[DB\_PROPERTY Function \[System\] for Data Lake Relational Engine](db-property-function-system-for-data-lake-relational-engine-a54c05b.md "Returns the value of the given property.")

[NEXT\_DATABASE Function \[System\] for Data Lake Relational Engine](next-database-function-system-for-data-lake-relational-engine-a5685c6.md "Returns the next database ID number, or the first database if the parameter is NULL.")

[OBJECT\_NAME Function \[System\] for Data Lake Relational Engine](object-name-function-system-for-data-lake-relational-engine-a56b844.md "Returns the object name.")

