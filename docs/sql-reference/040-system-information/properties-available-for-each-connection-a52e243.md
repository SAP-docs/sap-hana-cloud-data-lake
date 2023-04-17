<!-- loioa52e243684f21015a9ade02046fd07bb -->

# Properties Available for Each Connection

Retrieve the value of a specific connection property or the values of all connection properties.



Use the following to retrieve connection property information:

 `connection_property` system function
 :   Retrieves the value of a connection property. The following statement returns the number of pages that have been read from file by the current connection:

    ```
    select connection_property ( 'DiskRead' )
    ```

  `sa_conn_properties` system procedure
 :   Retrieves the values of all connection properties. The following statement returns separate row appears for each connection, for each property:

    ```
    call sa_conn_properties
    ```

 **Related Information**  


[Properties Available for Each Database](properties-available-for-each-database-a52f368.md "Retrieve the value of a specific database property or the values of all database properties. Database properties apply to an entire database.")

[CONNECTION\_PROPERTY Function \[System\] for Data Lake Relational Engine](../050-system-sql-functions/connection-property-function-system-for-data-lake-relational-engine-a53eeaf.md "Returns the value of a given connection property as a string.")

[PROPERTY Function \[System\] for Data Lake Relational Engine](../050-system-sql-functions/property-function-system-for-data-lake-relational-engine-a56fa4d.md "Returns the value of the specified server-level property as a string.")

[PROPERTY\_NAME Function \[System\] for Data Lake Relational Engine](../050-system-sql-functions/property-name-function-system-for-data-lake-relational-engine-a570a7e.md "Returns the name of the property with the supplied property number.")

[PROPERTY\_NUMBER Function \[System\] for Data Lake Relational Engine](../050-system-sql-functions/property-number-function-system-for-data-lake-relational-engine-a57131a.md "Returns the property number of the property with the supplied property name.")

