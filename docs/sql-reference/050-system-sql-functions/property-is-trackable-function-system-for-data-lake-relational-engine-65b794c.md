<!-- loio65b794ca66ab4b7fb8e60b888f9fc1f4 -->

# PROPERTY\_IS\_TRACKABLE Function \[System\] for Data Lake Relational Engine

Returns whether or not you can maintain historical data for the specified database server property by storing its tracked values.



```
PROPERTY_IS_TRACKABLE( <property-ID> )
```



## Parameters

  *<property-ID\>* 
 :   The PropNum of the database server property. You can find the PropNum of the database server property by running the sa\_eng\_properties system procedure or by calling the PROPERTY\_NUMBER function.

 

## Returns

1 if the database server property can be tracked; otherwise, returns 0.



## Remarks

Only database properties that return a numeric value can be tracked.



The following example returns all database server properties that are trackable:

```
SELECT PropName FROM sa_eng_properties( ) WHERE PROPERTY_IS_TRACKABLE( PropNum ) = 1;
```

