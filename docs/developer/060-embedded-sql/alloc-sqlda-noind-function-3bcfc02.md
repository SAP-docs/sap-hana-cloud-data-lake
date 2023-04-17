<!-- loio3bcfc0216c5f1014959ac7172e3f1c5c -->

# alloc\_sqlda\_noind Function

Allocate a SQLDA with no space for indicator variables.



```
struct sqlda * alloc_sqlda_noind( unsigned <numvar> );
```



## Parameters

numvar
:   The number of variable descriptors to allocate.



## Returns

Pointer to a SQLDA if successful and returns the null pointer if there is not enough memory available.



## Remarks

Allocates a SQLDA with descriptors for *<numvar\>* variables. The sqln field of the SQLDA is initialized to *<numvar\>*. Space is not allocated for indicator variables; the indicator pointers are set to the null pointer. A null pointer is returned if memory cannot be allocated.

