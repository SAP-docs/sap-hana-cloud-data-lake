<!-- loio3be1e5e26c5f1014aa0d8a5ef142426b -->

# Retrieving LONG Data Using Dynamic SQL

Retrieve a LONG VARCHAR, LONG NVARCHAR, or LONG BINARY value using dynamic SQL.



## Procedure

1.  Set the sqltype field to DT\_LONGVARCHAR, DT\_LONGNVARCHAR, or DT\_LONGBINARY as appropriate.

2.  Set the sqldata field to point to the LONGVARCHAR, LONGNVARCHAR, or LONGBINARY host variable structure.

    You can use the LONGVARCHARSIZE\(*<n\>*\), LONGNVARCHARSIZE\(*<n\>*\), or LONGBINARYSIZE\(*<n\>*\) macro to determine the total number of bytes to allocate to hold *<n\>* bytes of data in the array field.

3.  Set the array\_len field of the host variable structure to the number of bytes allocated for the array field.

4.  Retrieve the data using FETCH, GET DATA, or EXECUTE INTO. The following information is set:

     sqlind
     :   The sqlind field points to an indicator. The indicator value is negative if the value is NULL, 0 if there is no truncation, and is the positive untruncated length in bytes up to a maximum of 32767. If the indicator value is positive, use the untrunc\_len field instead.

      stored\_len
     :   The number of bytes stored in the array. Always less than or equal to array\_len and untrunc\_len.

      untrunc\_len
     :   The number of bytes that would be stored in the array if the value was not truncated. Always greater than or equal to stored\_len. If truncation occurs, this value is larger than array\_len.

      array
     :   This area contains the data fetched. The data is not null-terminated.

 


## Results

The LONG data is retrieved using dynamic SQL.



The following code fragment illustrates the mechanics of retrieving LONG VARCHAR data using dynamic Embedded SQL. It is not intended to be a practical application:

```
#define DATA_LEN 128000
void get_test_var()
{
  LONGVARCHAR *longptr;
  SQLDA       *sqlda;
  SQLVAR      *sqlvar;

  sqlda = alloc_sqlda( 1 );
  longptr = (LONGVARCHAR *)malloc(
               LONGVARCHARSIZE( DATA_LEN ) );
  if( sqlda == NULL || longptr == NULL ) 
  {
    fatal_error( "Allocation failed" );
  }

  // init longptr for receiving data
  longptr->array_len = DATA_LEN;

  // init sqlda for receiving data
  // (sqllen is unused with DT_LONG types)
  sqlda->sqld = 1; // using 1 sqlvar
  sqlvar = &sqlda->sqlvar[0];
  sqlvar->sqltype = DT_LONGVARCHAR;
  sqlvar->sqldata = longptr;
  printf( "fetching test_var\n" );
  EXEC SQL PREPARE select_stmt FROM 'SELECT test_var';
  EXEC SQL EXECUTE select_stmt INTO DESCRIPTOR sqlda;
  EXEC SQL DROP STATEMENT select_stmt;
  printf( "stored_len: %d, untrunc_len: %d, "
          "1st char: %c, last char: %c\n",
        longptr->stored_len,
        longptr->untrunc_len,
        longptr->array[0],
        longptr->array[DATA_LEN - 1] );
  free_sqlda( sqlda );
  free( longptr );
}
```

