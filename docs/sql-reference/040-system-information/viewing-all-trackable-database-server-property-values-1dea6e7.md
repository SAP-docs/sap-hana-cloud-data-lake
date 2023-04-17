<!-- loio1dea6e7484834687b5a7b07ee8c3c531 -->

# Viewing All Trackable Database Server Property Values

View the list of database server property values that can be tracked.



## Context

Only database server properties with numeric values can be tracked.

You can find the PropNum of the database server property by running the sa\_eng\_properties system procedure or by calling the PROPERTY\_NUMBER function.



## Procedure

Execute the following statement:

```
SELECT * FROM sa_eng_properties()
WHERE PROPERTY_IS_TRACKABLE( PropNum ) = 1;
```



## Results

The list of database server properties that can be tracked is returned.

**Related Information**  


[sa\_eng\_properties System Procedure for Data Lake Relational Engine](../060-stored-procedures/sa-eng-properties-system-procedure-for-data-lake-relational-engine-3be5bff.md "Reports database server property information.")

[PROPERTY\_NUMBER Function \[System\] for Data Lake Relational Engine](../050-system-sql-functions/property-number-function-system-for-data-lake-relational-engine-a57131a.md "Returns the property number of the property with the supplied property name.")

