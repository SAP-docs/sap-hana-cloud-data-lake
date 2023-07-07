<!-- loioa52f368484f210159014ec802d5ab34f -->

# Properties Available for Each Database

Retrieve the value of a specific database property or the values of all database properties. Database properties apply to an entire database.

The server properties QueryBypassedCosted, QueryBypassedOptimized, QueryDescribedOptimizer, and StatementPostAnnotatesSimple are updated only for queries against catalog store tables.

Use the following to retrieve database property information:


<dl>
<dt><b>

`db_property` system function

</b></dt>
<dd>

Retrieves the value of a database property. The following statement returns the page size of the current database:

```
select db_property ( 'PageSize')
```



</dd><dt><b>

`sa_db_properties` system procedure

</b></dt>
<dd>

Retrieves the values of all database properties:

```
call sa_db_properties
```



</dd>
</dl>

**Related Information**  


[Properties Available for the Server](properties-available-for-the-server-a52ea6d.md "Retrieve the value of a specific server property or the values of all server properties.")

[Properties Available for Each Connection](properties-available-for-each-connection-a52e243.md "Retrieve the value of a specific connection property or the values of all connection properties.")

[CONNECTION\_PROPERTY Function \[System\] for Data Lake Relational Engine](050-system-sql-functions/connection-property-function-system-for-data-lake-relational-engine-a53eeaf.md "Returns the value of a given connection property as a string.")

[PROPERTY Function \[System\] for Data Lake Relational Engine](050-system-sql-functions/property-function-system-for-data-lake-relational-engine-a56fa4d.md "Returns the value of the specified server-level property as a string.")

[PROPERTY\_NAME Function \[System\] for Data Lake Relational Engine](050-system-sql-functions/property-name-function-system-for-data-lake-relational-engine-a570a7e.md "Returns the name of the property with the supplied property number.")

[PROPERTY\_NUMBER Function \[System\] for Data Lake Relational Engine](050-system-sql-functions/property-number-function-system-for-data-lake-relational-engine-a57131a.md "Returns the property number of the property with the supplied property name.")

