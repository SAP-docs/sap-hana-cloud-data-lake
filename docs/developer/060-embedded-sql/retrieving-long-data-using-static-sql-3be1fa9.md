<!-- loio3be1fa986c5f1014b3ff8b5afe1ace30 -->

# Retrieving LONG Data Using Static SQL

Retrieve a LONG VARCHAR, LONG NVARCHAR, or LONG BINARY value using static SQL.



## Procedure

1.  Declare a host variable of type DECL\_LONGVARCHAR, DECL\_LONGNVARCHAR, or DECL\_LONGBINARY, as appropriate. The array\_len field is filled in automatically.

2.  Retrieve the data using FETCH, GET DATA, or EXECUTE INTO. The following information is set:

     sqlind
     :   The sqlind field points to an indicator. The indicator value is negative if the value is NULL, 0 if there is no truncation, and is the positive untruncated length in bytes up to a maximum of 32767. If the indicator value is positive, use the untrunc\_len field instead.

      stored\_len
     :   The number of bytes stored in the array. Always less than or equal to array\_len and untrunc\_len.

      untrunc\_len
     :   The number of bytes that would be stored in the array if the value was not truncated. Always greater than or equal to stored\_len. If truncation occurs, this value is larger than array\_len.

      array
     :   This area contains the data fetched. The data is not null-terminated.

 


## Results

The LONG data is retrieved using static SQL.



The following code fragment illustrates the mechanics of retrieving a LONG VARCHAR using static Embedded SQL. It is not intended to be a practical application.

```
EXEC SQL BEGIN DECLARE SECTION;
// SQLPP initializes longdata.array_len to 128K
DECL_LONGVARCHAR(131072) longdata;
EXEC SQL END DECLARE SECTION;

// Init longdata for fetching data, not required
// since these fields are updated by FETCH
longdata.stored_len = 0;
longdata.untrunc_len = 0;
memset( longdata.array, 0, 131072 );
EXEC SQL FETCH ABSOLUTE 1 c1 INTO :longdata;
printf( "Length fetched %d, Actual length %d, Data[0..19] \"%20.20s\"\n",
    longdata.stored_len, longdata.untrunc_len, longdata.array );
```

