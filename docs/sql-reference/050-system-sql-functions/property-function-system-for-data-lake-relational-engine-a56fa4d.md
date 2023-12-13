<!-- loioa56fa4db84f2101581d1eea9ca3957e2 -->

# PROPERTY Function \[System\] for Data Lake Relational Engine

Returns the value of the specified server-level property as a string.



```
PROPERTY ( { <property-id> | <property-name> } );
```



<a name="loioa56fa4db84f2101581d1eea9ca3957e2__iq_refbb_871"/>

## Parameters


<dl>
<dt><b>

*<property-id\>*

</b></dt>
<dd>

An integer that is the property-number of the server-level property. This number can be determined from the `PROPERTY_NUMBER` function. The *<property-id\>* is commonly used when looping through a set of properties.



</dd><dt><b>

*<property-name\>*

</b></dt>
<dd>

A string giving the name of the property.



</dd>
</dl>



## Result Set

VARCHAR



<a name="loioa56fa4db84f2101581d1eea9ca3957e2__iq_refbb_874"/>

## Remarks

> ### Note:  
> CIS functional compensation performance considerations apply.

Each property has both a number and a name, but the number is subject to change between versions, and should not be used as a reliable identifier for a given property.



<a name="loioa56fa4db84f2101581d1eea9ca3957e2__iq_refbb_875"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loioa56fa4db84f2101581d1eea9ca3957e2__iq_refbb_873"/>

## Example

The following statement returns the name of the current database server:

```
SELECT PROPERTY( 'Name' ) FROM iq_dummy;
```

**Related Information**  


[Properties Available for the Server](../properties-available-for-the-server-a52ea6d.md "Retrieve the value of a specific server property or the values of all server properties.")

[Properties Available for Each Database](../properties-available-for-each-database-a52f368.md "Retrieve the value of a specific database property or the values of all database properties. Database properties apply to an entire database.")

[Properties Available for Each Connection](../properties-available-for-each-connection-a52e243.md "Retrieve the value of a specific connection property or the values of all connection properties.")

[CONNECTION\_PROPERTY Function \[System\] for Data Lake Relational Engine](connection-property-function-system-for-data-lake-relational-engine-a53eeaf.md "Returns the value of a given connection property as a string.")

[PROPERTY\_NAME Function \[System\] for Data Lake Relational Engine](property-name-function-system-for-data-lake-relational-engine-a570a7e.md "Returns the name of the property with the supplied property number.")

[PROPERTY\_NUMBER Function \[System\] for Data Lake Relational Engine](property-number-function-system-for-data-lake-relational-engine-a57131a.md "Returns the property number of the property with the supplied property name.")

