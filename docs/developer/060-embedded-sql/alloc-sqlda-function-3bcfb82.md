<!-- loio3bcfb82e6c5f10149e33bd5cbf6e928c -->

# alloc\_sqlda Function

Allocate a SQLDA.



```
struct sqlda * alloc_sqlda( unsigned <numvar> );
```



## Parameters

numvar
:   The number of variable descriptors to allocate.



## Returns

Pointer to a SQLDA if successful and returns the null pointer if there is not enough memory available.



## Remarks

Allocates a SQLDA with descriptors for *<numvar\>* variables. The sqln field of the SQLDA is initialized to *<numvar\>*. Space is allocated for the indicator variables, the indicator pointers are set to point to this space, and the indicator value is initialized to zero. A null pointer is returned if memory cannot be allocated. Use this function instead of the alloc\_sqlda\_noind function.

