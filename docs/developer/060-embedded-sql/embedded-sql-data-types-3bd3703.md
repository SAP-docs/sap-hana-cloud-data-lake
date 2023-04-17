<!-- loio3bd370336c5f1014b710b4d4c8678d69 -->

# Embedded SQL Data Types

To transfer information between a program and the database server, every piece of data must have a data type.



The Embedded SQL data type constants are prefixed with DT\_, and can be found in the `sqldef.h` header file. You can create a host variable of any one of the supported types. You can also use these types in a SQLDA structure for passing data to and from the database.

You can define variables of these data types using the DECL\_ macros listed in `sqlca.h`. For example, a variable holding a BIGINT value could be declared with DECL\_BIGINT.

The following data types are supported by the Embedded SQL programming interface:

 DT\_BIT
 :   8-bit signed integer.

  DT\_SMALLINT
 :   16-bit signed integer.

  DT\_UNSSMALLINT
 :   16-bit unsigned integer.

  DT\_TINYINT
 :   8-bit signed integer.

  DT\_BIGINT
 :   64-bit signed integer.

  DT\_UNSBIGINT
 :   64-bit unsigned integer.

  DT\_INT
 :   32-bit signed integer.

  DT\_UNSINT
 :   32-bit unsigned integer.

  DT\_FLOAT
 :   4-byte floating-point number.

  DT\_DOUBLE
 :   8-byte floating-point number.

  DT\_DECIMAL
 :   Packed decimal number \(proprietary format\).

    ```
    typedef struct TYPE_DECIMAL {
      char array[1];
    } TYPE_DECIMAL;
    ```

  DT\_STRING
 :   Null-terminated character string, in the CHAR character set. The string is blank-padded if the database is initialized with blank-padded strings.

  DT\_NSTRING
 :   Null-terminated character string, in the NCHAR character set. The string is blank-padded if the database is initialized with blank-padded strings.

  DT\_DATE
 :   Null-terminated character string that is a valid date.

  DT\_TIME
 :   Null-terminated character string that is a valid time.

  DT\_TIMESTAMP
 :   Null-terminated character string that is a valid timestamp.

  DT\_FIXCHAR
 :   Fixed-length blank-padded character string, in the CHAR character set. The maximum length, specified in bytes, is 32767. The data is not null-terminated.

  DT\_NFIXCHAR
 :   Fixed-length blank-padded character string, in the NCHAR character set. The maximum length, specified in bytes, is 32767. The data is not null-terminated.

  DT\_VARCHAR
 :   Varying length character string, in the CHAR character set, with a two-byte length field. When sending data, you must set the length field. The maximum length that can be sent is 32767 bytes. When fetching data, the database server sets the length field. The maximum length that can be fetched is 32767 bytes. The data is not null-terminated or blank-padded. The sqldata field points to this data area that is exactly sqllen + 2 bytes long.

    ```
    typedef struct VARCHAR {
     a_sql_ulen len;
     char       array[1];
    } VARCHAR;
    ```

  DT\_NVARCHAR
 :   Varying length character string, in the NCHAR character set, with a two-byte length field. When sending data, you must set the length field. The maximum length that can be sent is 32767 bytes. When fetching data, the database server sets the length field. The maximum length that can be fetched is 32767 bytes. The data is not null-terminated or blank-padded. The sqldata field points to this data area that is exactly sqllen + 2 bytes long.

    ```
    typedef struct NVARCHAR {
     a_sql_ulen len;
     char       array[1];
    } NVARCHAR;
    ```

  DT\_LONGVARCHAR
 :   Long varying length character string, in the CHAR character set.

    ```
    typedef struct LONGVARCHAR {
     a_sql_uint32 array_len;  /* number of allocated bytes in array */
     a_sql_uint32 stored_len; /* number of bytes stored in array
                               * (never larger than array_len) */
     a_sql_uint32 untrunc_len;/* number of bytes in untruncated expression
                               * (may be larger than array_len) */
     char         array[1];   /* the data */
    } LONGVARCHAR, LONGNVARCHAR, LONGBINARY;
    ```

    The LONGVARCHAR structure can be used with more than 32767 bytes of data. Large data can be fetched all at once, or in pieces using the GET DATA statement. Large data can be supplied to the server all at once, or in pieces by appending to a database variable using the SET statement. The data is not null-terminated or blank-padded.

  DT\_LONGNVARCHAR
 :   Long varying length character string, in the NCHAR character set. The macro defines a structure, as follows:

    ```
    typedef struct LONGVARCHAR {
     a_sql_uint32 array_len;  /* number of allocated bytes in array */
     a_sql_uint32 stored_len; /* number of bytes stored in array
                               * (never larger than array_len) */
     a_sql_uint32 untrunc_len;/* number of bytes in untruncated expression
                               * (may be larger than array_len) */
     char         array[1];   /* the data */
    } LONGVARCHAR, LONGNVARCHAR, LONGBINARY;
    ```

    The LONGNVARCHAR structure can be used with more than 32767 bytes of data. Large data can be fetched all at once, or in pieces using the GET DATA statement. Large data can be supplied to the server all at once, or in pieces by appending to a database variable using the SET statement. The data is not null-terminated or blank-padded.

  DT\_BINARY
 :   Varying length binary data with a two-byte length field. When sending data, you must set the length field. The maximum length that can be sent is 32767 bytes. When fetching data, the database server sets the length field. The maximum length that can be fetched is 32767 bytes. The data is not null-terminated or blank-padded. The sqldata field points to this data area that is exactly sqllen + 2 bytes long.

    ```
    typedef struct BINARY {
     a_sql_ulen len;
     char       array[1];
    } BINARY;
    ```

  DT\_LONGBINARY
 :   Long binary data. The macro defines a structure, as follows:

    ```
    typedef struct LONGVARCHAR {
     a_sql_uint32 array_len;  /* number of allocated bytes in array */
     a_sql_uint32 stored_len; /* number of bytes stored in array
                               * (never larger than array_len) */
     a_sql_uint32 untrunc_len;/* number of bytes in untruncated expression
                               * (may be larger than array_len) */
     char         array[1];   /* the data */
    } LONGVARCHAR, LONGNVARCHAR, LONGBINARY;
    ```

    The LONGBINARY structure can be used with more than 32767 bytes of data. Large data can be fetched all at once, or in pieces using the GET DATA statement. Large data can be supplied to the server all at once, or in pieces by appending to a database variable using the SET statement.

  DT\_TIMESTAMP\_STRUCT
 :   SQLDATETIME structure with fields for each part of a timestamp.

    ```
    typedef struct sqldatetime {
     unsigned short year; /* for example 1999 */
     unsigned char  month; /* 0-11 */
     unsigned char  day_of_week; /* 0-6 0=Sunday */
     unsigned short day_of_year; /* 0-365 */
     unsigned char  day; /* 1-31 */
     unsigned char  hour; /* 0-23 */
     unsigned char  minute; /* 0-59 */
     unsigned char  second; /* 0-59 */
     unsigned long  microsecond; /* 0-999999 */
    } SQLDATETIME;
    ```

    The SQLDATETIME structure can be used to retrieve fields of DATE, TIME, and TIMESTAMP type \(or anything that can be converted to one of these\). Often, applications have their own formats and date manipulation code. Fetching data in this structure makes it easier for you to manipulate this data. DATE, TIME, and TIMESTAMP fields can also be fetched and updated with any character type.

    If you use a SQLDATETIME structure to enter a date, time, or timestamp into the database, the day\_of\_year and day\_of\_week members are ignored.

  DT\_VARIABLE
 :   Null-terminated character string. The character string must be the name of a SQL variable whose value is used by the database server. This data type is used only for supplying data to the database server. It cannot be used when fetching data from the database server.

 The structures are defined in the `sqlca.h` file. The VARCHAR, NVARCHAR, BINARY, DECIMAL, and LONG data types are not useful for declaring host variables because they contain a one-character array. However, they are useful for allocating variables dynamically or typecasting other variables.



## DATE and TIME Database Types

There are no corresponding Embedded SQL interface data types for the various DATE and TIME database types. These database types are all fetched and updated using either the SQLDATETIME structure or character strings.

