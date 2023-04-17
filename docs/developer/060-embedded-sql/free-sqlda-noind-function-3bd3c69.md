<!-- loio3bd3c69f6c5f1014a1a7f0853608b6bb -->

# free\_sqlda\_noind Function

Free memory allocated to a SQLDA, ignoring indicator variable pointers.



```
void free_sqlda_noind( struct sqlda * <sqlda> );
```



## Parameters

sqlda
:   A pointer to a SQLDA structure.



## Remarks

Free space allocated to this *<sqlda\>*. Do not free the memory referenced by each sqldata pointer. The indicator variable pointers are ignored.

