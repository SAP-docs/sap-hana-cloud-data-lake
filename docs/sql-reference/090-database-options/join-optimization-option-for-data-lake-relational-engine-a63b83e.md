<!-- loioa63b83eb84f2101588769b704ce957b7 -->

# JOIN\_OPTIMIZATION Option for Data Lake Relational Engine

Enables or disables the optimization of the join order.



> ### Restriction:  
> This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa63b83eb84f2101588769b704ce957b7__iq_refso_664"/>

## Default

ON



<a name="loioa63b83eb84f2101588769b704ce957b7__iq_refso_666"/>

## Remarks

When JOIN\_OPTIMIZATION is ON, data lake Relational Engine optimizes the join order to reduce the size of intermediate results and sorts, and to balance the system load.

JOIN\_OPTIMIZATION controls the order of the joins, but not the order of the tables. To show the distinction, consider this example FROM clause with four tables:

```
FROM  A, B, C, D
```

By default, this FROM clause creates a left deep plan of joins that could also be explicitly represented as:

```
FROM  (((A, B), C), D)
```

