<!-- loioa570a7e184f2101584578b1e641ba61b -->

# PROPERTY\_NAME Function \[System\] for Data Lake Relational Engine

Returns the name of the property with the supplied property number.



```
PROPERTY_NAME ( <property-id> )
```



<a name="loioa570a7e184f2101584578b1e641ba61b__iq_refbb_883"/>

## Parameters

 *<property-id\>*
 :   The property number of the property.

 

## Returns

VARCHAR



<a name="loioa570a7e184f2101584578b1e641ba61b__section_pc3_s44_qbb"/>

## Remarks

> ### Note:  
> CIS functional compensation performance considerations apply.



<a name="loioa570a7e184f2101584578b1e641ba61b__iq_refbb_886"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loioa570a7e184f2101584578b1e641ba61b__iq_refbb_885"/>

## Example

The following statement returns the property associated with property number 126:

```
SELECT PROPERTY_NAME( 126 ) FROM iq_dummy
```

The actual property to which this refers changes from version to version.

**Related Information**  


[Properties Available for the Server](../040-system-information/properties-available-for-the-server-a52ea6d.md "Retrieve the value of a specific server property or the values of all server properties.")

[Properties Available for Each Database](../040-system-information/properties-available-for-each-database-a52f368.md "Retrieve the value of a specific database property or the values of all database properties. Database properties apply to an entire database.")

[Properties Available for Each Connection](../040-system-information/properties-available-for-each-connection-a52e243.md "Retrieve the value of a specific connection property or the values of all connection properties.")

[CONNECTION\_PROPERTY Function \[System\] for Data Lake Relational Engine](connection-property-function-system-for-data-lake-relational-engine-a53eeaf.md "Returns the value of a given connection property as a string.")

[PROPERTY Function \[System\] for Data Lake Relational Engine](property-function-system-for-data-lake-relational-engine-a56fa4d.md "Returns the value of the specified server-level property as a string.")

[PROPERTY\_NUMBER Function \[System\] for Data Lake Relational Engine](property-number-function-system-for-data-lake-relational-engine-a57131a.md "Returns the property number of the property with the supplied property name.")

