<!-- loioa52ea6de84f21015a4708b28bf33538e -->

# Properties Available for the Server

Retrieve the value of a specific server property or the values of all server properties.

Server properties apply across the server as a whole.

Use the following to retrieve the value of a server property:

 `property` system function
 :   Retrieves the value of a server property. The following statement returns the number of cache pages being used to hold the main heap:

    ```
    select property ( 'MainHeapPages') from iq_dummy
    ```

  `sa_eng_properties` system procedure
 :   Retrieves the values of all server properties:

    ```
    call sa_eng_properties
    ```

 **Related Information**  


[Properties Available for Each Database](properties-available-for-each-database-a52f368.md "Retrieve the value of a specific database property or the values of all database properties. Database properties apply to an entire database.")

[Properties Available for Each Connection](properties-available-for-each-connection-a52e243.md "Retrieve the value of a specific connection property or the values of all connection properties.")

[CONNECTION\_PROPERTY Function \[System\] for Data Lake Relational Engine](../050-system-sql-functions/connection-property-function-system-for-data-lake-relational-engine-a53eeaf.md "Returns the value of a given connection property as a string.")

[PROPERTY Function \[System\] for Data Lake Relational Engine](../050-system-sql-functions/property-function-system-for-data-lake-relational-engine-a56fa4d.md "Returns the value of the specified server-level property as a string.")

[PROPERTY\_NAME Function \[System\] for Data Lake Relational Engine](../050-system-sql-functions/property-name-function-system-for-data-lake-relational-engine-a570a7e.md "Returns the name of the property with the supplied property number.")

[PROPERTY\_NUMBER Function \[System\] for Data Lake Relational Engine](../050-system-sql-functions/property-number-function-system-for-data-lake-relational-engine-a57131a.md "Returns the property number of the property with the supplied property name.")

