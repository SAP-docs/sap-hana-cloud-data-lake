<!-- loioa57131a184f2101585959e45321b1e95 -->

# PROPERTY\_NUMBER Function \[System\] for Data Lake Relational Engine

Returns the property number of the property with the supplied property name.



```
PROPERTY_NUMBER ( <property-name> );
```



<a name="loioa57131a184f2101585959e45321b1e95__iq_refbb_888"/>

## Parameters


<dl>
<dt><b>

*<property-name\>*

</b></dt>
<dd>

A property name.



</dd>
</dl>



## Result Set

INT



<a name="loioa57131a184f2101585959e45321b1e95__section_uby_n44_qbb"/>

## Remarks

> ### Note:  
> CIS functional compensation performance considerations apply.



<a name="loioa57131a184f2101585959e45321b1e95__iq_refbb_891"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loioa57131a184f2101585959e45321b1e95__iq_refbb_890"/>

## Examples

The following statement returns an integer value:

```
SELECT PROPERTY_NUMBER( 'PAGESIZE' ) FROM iq_dummy;
```

The actual value changes from version to version.

**Related Information**  


[Properties Available for the Server](../properties-available-for-the-server-a52ea6d.md "Retrieve the value of a specific server property or the values of all server properties.")

[Properties Available for Each Database](../properties-available-for-each-database-a52f368.md "Retrieve the value of a specific database property or the values of all database properties. Database properties apply to an entire database.")

[Properties Available for Each Connection](../properties-available-for-each-connection-a52e243.md "Retrieve the value of a specific connection property or the values of all connection properties.")

[CONNECTION\_PROPERTY Function \[System\] for Data Lake Relational Engine](connection-property-function-system-for-data-lake-relational-engine-a53eeaf.md "Returns the value of a given connection property as a string.")

[PROPERTY Function \[System\] for Data Lake Relational Engine](property-function-system-for-data-lake-relational-engine-a56fa4d.md "Returns the value of the specified server-level property as a string.")

[PROPERTY\_NAME Function \[System\] for Data Lake Relational Engine](property-name-function-system-for-data-lake-relational-engine-a570a7e.md "Returns the name of the property with the supplied property number.")

