<!-- loio3bd3b6fe6c5f1014a5fdac2aa43c9582 -->

# free\_filled\_sqlda Function

Free memory allocated to each sqldata pointer and the space allocated for the SQLDA itself.



```
void free_filled_sqlda( struct sqlda * <sqlda> );
```



## Parameters

sqlda
:   A pointer to a SQLDA structure.



## Remarks

Free the memory allocated to each sqldata pointer and the space allocated for the SQLDA itself. Any null pointer is not freed.

This should only be called if fill\_sqlda, fill\_sqlda\_ex, or fill\_s\_sqlda was used to allocate the sqldata fields of the SQLDA.

Calling this function causes free\_sqlda to be called automatically, and so any descriptors allocated by alloc\_sqlda are freed.

