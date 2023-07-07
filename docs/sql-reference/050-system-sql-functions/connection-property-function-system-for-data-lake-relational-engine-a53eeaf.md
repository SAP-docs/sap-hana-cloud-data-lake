<!-- loioa53eeaf984f21015974f97e3388d1738 -->

# CONNECTION\_PROPERTY Function \[System\] for Data Lake Relational Engine

Returns the value of a given connection property as a string.



```
CONNECTION_PROPERTY ( { <integer-expression1> | <string-expression> }
… [ , <integer-expression2> ] )
```



<a name="loioa53eeaf984f21015974f97e3388d1738__iq_refbb_327"/>

## Parameters


<dl>
<dt><b>

*<integer-expression1\>*

</b></dt>
<dd>

In most cases, it is more convenient to supply a string expression as the first argument. If you do supply integer-expression1, it is the connection property ID. You can determine this using the PROPERTY\_NUMBER function.



</dd><dt><b>

*<string-expression\>*

</b></dt>
<dd>

The connection property name. Specify either the property ID or the property name.



</dd><dt><b>

*<integer-expression2\>*

</b></dt>
<dd>

The connection ID of the current database connection. The current connection is used if this argument is omitted.



</dd>
</dl>



## Returns

VARCHAR



<a name="loioa53eeaf984f21015974f97e3388d1738__iq_refbb_330"/>

## Remarks

> ### Note:  
> CIS functional compensation performance considerations apply.

The current connection is used if the second argument is omitted.



<a name="loioa53eeaf984f21015974f97e3388d1738__iq_refbb_331"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa53eeaf984f21015974f97e3388d1738__iq_refbb_329"/>

## Example

The following statement returns 4, the number of prepared statements being maintained:

```
SELECT connection_property( 'PrepStmt' )FROM iq_dummy
```

**Related Information**  


[Properties Available for the Server](../properties-available-for-the-server-a52ea6d.md "Retrieve the value of a specific server property or the values of all server properties.")

[Properties Available for Each Database](../properties-available-for-each-database-a52f368.md "Retrieve the value of a specific database property or the values of all database properties. Database properties apply to an entire database.")

[Properties Available for Each Connection](../properties-available-for-each-connection-a52e243.md "Retrieve the value of a specific connection property or the values of all connection properties.")

[PROPERTY Function \[System\] for Data Lake Relational Engine](property-function-system-for-data-lake-relational-engine-a56fa4d.md "Returns the value of the specified server-level property as a string.")

[PROPERTY\_NAME Function \[System\] for Data Lake Relational Engine](property-name-function-system-for-data-lake-relational-engine-a570a7e.md "Returns the name of the property with the supplied property number.")

[PROPERTY\_NUMBER Function \[System\] for Data Lake Relational Engine](property-number-function-system-for-data-lake-relational-engine-a57131a.md "Returns the property number of the property with the supplied property name.")

[sp\_iqshowpsexe Procedure for Data Lake Relational Engine](../060-stored-procedures/sp-iqshowpsexe-procedure-for-data-lake-relational-engine-a5b64f1.md "Displays information about the settings of database options that control the priority of tasks and resource usage for connections.")

