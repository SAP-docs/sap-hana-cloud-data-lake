<!-- loiofeb0bd7b4c304ff1af05d83eee2f26bb -->

# DBRealloc Function

Reallocate memory for a SQLDA variable.



```
void * DBRealloc( void * <ptr>, size_t <size> );
```



## Parameters

 ptr
 :   Pointer to the memory allocated by a previous call to the DBAlloc or DBRealloc function.

  size
 :   The number of bytes to allocate.

 

## Returns

DBRealloc returns a void pointer to the allocated space, or NULL if there is insufficient memory available.



## Remarks

Use this function to reallocate memory for Embedded SQL data areas.



In this example, assume that the third column has sqltype DT\_LONGVARCHAR. Since fill\_sqlda allocates at most 32767 bytes of memory for the data area, the data area is reallocated for a maximum size string of 100K bytes. The LONGVARCHAR data structure is initialized. A subsequent call to the free\_filled\_sqlda function will release this new data area.

```
#define MAXLEN (100*1024)
LONGVARCHAR *lvcdata;

fill_sqlda( sqlda );

sqlda->sqlvar[ 2 ].sqldata = DBRealloc( sqlda->sqlvar[ 2 ].sqldata, LONGVARCHARSIZE(MAXLEN) );
lvcdata = (LONGVARCHAR *)sqlda->sqlvar[ 2 ].sqldata;
lvcdata->array_len = MAXLEN;
lvcdata->stored_len = 0;
lvcdata->untrunc_len = 0;
```

