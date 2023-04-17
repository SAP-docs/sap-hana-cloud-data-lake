<!-- loioc9dc72574d4e4e4d96ac9aa4d818b929 -->

# DBAlloc Function

Allocate memory for a SQLDA variable.



```
void * DBAlloc( size_t <size> );
```



## Parameters

 size
 :   The number of bytes to allocate.

 

## Returns

DBAlloc returns a void pointer to the allocated space, or NULL if there is insufficient memory available.



## Remarks

Use this function to allocate memory for Embedded SQL data areas.



In this example, assume that the third column has sqltype DT\_LONGVARCHAR. Since fill\_sqlda allocates at most 32767 bytes of memory for the data area, the data area is released and a new area is allocated for a maximum size string of 100K bytes. The LONGVARCHAR data structure is initialized. A subsequent call to the free\_filled\_sqlda function will release this new data area.

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

