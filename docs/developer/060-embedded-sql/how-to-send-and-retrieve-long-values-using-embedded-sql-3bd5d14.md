<!-- loio3bd5d14c6c5f1014ba56a326504b3fb5 -->

# How to Send and Retrieve Long Values Using Embedded SQL

The method for sending and retrieving LONG VARCHAR, LONG NVARCHAR, and LONG BINARY values in Embedded SQL applications is different from that for other data types.

The standard SQLDA fields are limited to 32767 bytes of data as the fields holding the length information \(sqllen, \*sqlind\) are 16-bit values. Changing these values to 32-bit values would break existing applications.

The method of describing LONG VARCHAR, LONG NVARCHAR, and LONG BINARY values is the same as for other data types.



## Static SQL Structures

Separate fields are used to hold the allocated, stored, and untruncated lengths of LONG BINARY, LONG VARCHAR, and LONG NVARCHAR data types. The static SQL data types are defined in `sqlca.h` as follows:

```
#define DECL_LONGVARCHAR( size )         \
  struct { a_sql_uint32    array_len;    \
           a_sql_uint32    stored_len;   \
           a_sql_uint32    untrunc_len;  \
           char            array[size+1];\
         }
#define DECL_LONGNVARCHAR( size )        \
  struct { a_sql_uint32    array_len;    \
           a_sql_uint32    stored_len;   \
           a_sql_uint32    untrunc_len;  \
           char            array[size+1];\
         }
#define DECL_LONGBINARY( size )          \
  struct { a_sql_uint32    array_len;    \
           a_sql_uint32    stored_len;   \
           a_sql_uint32    untrunc_len;  \
           char            array[size];  \
         }
```

The `size+1` allocation does not indicate that the LONGVARCHAR/LONGNVARCHAR `array` is null-terminated by the client library. The extra byte is included for those applications that wish to null-terminate the chunk that has been fetched from the database. Use the `stored_len` field to determine the amount of data fetched.

When any of these macros are used in an Embedded SQL DECLARE SECTION, the `array_len` field is initialized to `size`. Otherwise, the `array_len` field is not initialized.



## Dynamic SQL Structures

For dynamic SQL, set the sqltype field to DT\_LONGVARCHAR, DT\_LONGNVARCHAR, or DT\_LONGBINARY as appropriate. The associated LONGVARCHAR, LONGNVARCHAR, and LONGBINARY structure is as follows:

```
typedef struct LONGVARCHAR {
    a_sql_uint32    array_len;
    a_sql_uint32    stored_len;
    a_sql_uint32    untrunc_len;
    char            array[1];
} LONGVARCHAR, LONGNVARCHAR, LONGBINARY;
```



## Structure Member Definitions

For both static and dynamic SQL structures, the structure members are defined as follows:

 array\_len
 :   \(Sending and retrieving.\) The number of bytes allocated for the array part of the structure.

  stored\_len
 :   \(Sending and retrieving.\) The number of bytes stored in the array. Always less than or equal to array\_len and untrunc\_len.

  untrunc\_len
 :   \(Retrieving only.\) The number of bytes that would be stored in the array if the value was not truncated. Always greater than or equal to stored\_len. If truncation occurs, this value is larger than array\_len.

 