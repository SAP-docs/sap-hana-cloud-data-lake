<!-- loio3bd3beb56c5f101481a2ce627564e6c7 -->

# free\_sqlda Function

Free memory allocated to a SQLDA.



```
void free_sqlda( struct sqlda * <sqlda> );
```



## Parameters

sqlda
:   A pointer to a SQLDA structure.



## Remarks

Free space allocated to this *<sqlda\>* and free the indicator variable space, as allocated in fill\_sqlda. Do not free the memory referenced by each sqldata pointer.

