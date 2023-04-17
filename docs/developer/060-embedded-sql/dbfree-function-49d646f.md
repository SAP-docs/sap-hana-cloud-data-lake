<!-- loio49d646f44977441f8e6afd0ffde9fbd3 -->

# DBFree Function

Free memory the was allocated using DBAlloc or DBRealloc.



```
void DBFree( void * <ptr> );
```



## Parameters

 ptr
 :   Pointer to the memory allocated by the DBAlloc or DBRealloc function.

 

## Remarks

Use this function to free memory for Embedded SQL data areas.



In this example, assume that the third column has sqltype DT\_LONGVARCHAR. Since fill\_sqlda allocates at most 32767 bytes of memory for the data area, the data area is released and reallocated for a maximum size string of 100K bytes. The LONGVARCHAR data structure is initialized. A subsequent call to the free\_filled\_sqlda function will release this new data area.

```
#define MAXLEN (100*1024)
LONGVARCHAR *lvcdata;

fill_sqlda( sqlda );

DBFree( sqlda->sqlvar[ 2 ].sqldata );
sqlda->sqlvar[ 2 ].sqldata = DBAlloc( LONGVARCHARSIZE(MAXLEN) );
lvcdata = (LONGVARCHAR *)sqlda->sqlvar[ 2 ].sqldata;
lvcdata->array_len = MAXLEN;
lvcdata->stored_len = 0;
lvcdata->untrunc_len = 0;
```

