<!-- loioa57024b884f21015a1819d79e3571f53 -->

# PROPERTY\_DESCRIPTION Function \[System\] for Data Lake Relational Engine

Returns a description of a property.



```
PROPERTY_DESCRIPTION ( { <property-id> | <property-name> } )
```



<a name="loioa57024b884f21015a1819d79e3571f53__iq_refbb_877"/>

## Parameters

 *<property-id\>*
 :   An integer that is the property number of the property. This number can be determined from the `PROPERTY_NUMBER` function. The *<property-id\>* is commonly used when looping through a set of properties.

  *<property-name\>*
 :   A string giving the name of the property.

 

## Returns

VARCHAR



<a name="loioa57024b884f21015a1819d79e3571f53__iq_refbb_880"/>

## Remarks

> ### Note:  
> CIS functional compensation performance considerations apply.

Each property has both a number and a name, but the number is subject to change between releases, and should not be used as a reliable identifier for a given property.



<a name="loioa57024b884f21015a1819d79e3571f53__iq_refbb_881"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loioa57024b884f21015a1819d79e3571f53__iq_refbb_879"/>

## Example

The following statement returns the description "Number of index insertions":

```
SELECT PROPERTY_DESCRIPTION( 'IndAdd' ) FROM iq_dummy
```

