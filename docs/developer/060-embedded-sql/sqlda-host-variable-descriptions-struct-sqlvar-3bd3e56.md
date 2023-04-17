<!-- loio3bd3e56a6c5f1014aa3ad0ed8ac429d3 -->

# SQLDA Host Variable Descriptions \(struct sqlvar\)

Each sqlvar structure in the SQLDA describes a host variable.



The fields of the sqlvar structure are defined in the `sqlda.h` header file and have the following meanings:

sqltype
:   The type and flags of the variable that is described by this descriptor. The type is extracted using DT\_TYPES and the flags are extracted using DT\_FLAGS.

    ```
    a_sql_type sql_type = sqlvar->sqltype & DT_TYPES;
    a_sql_type sql_flag = sqlvar->sqltype & DT_FLAGS;
    ```

    The DT\_NULLS\_ALLOWED bit of the flags indicates whether NULL values are allowed. Valid types and flags are defined in the `sqlhosttype.h` header file.

    This field is filled by the DESCRIBE statement. You can change this field to any type when supplying data to the database server or retrieving data from the database server as long as the sqldata field is changed accordingly to match the new type. Any necessary type conversion is done automatically \(for example, binary integer to ASCII string\).

sqllen
:   The length of the variable. A sqllen value has type a\_sql\_len. What the length actually means depends on the type information and how the SQLDA is being used.

    For LONG VARCHAR, LONG NVARCHAR, and LONG BINARY data types, the array\_len field of the LONGVARCHAR, LONGNVARCHAR, or LONGBINARY data type structure is used instead of the sqllen field. In these cases, sqllen is usually set to 32767 \(the maximum\).

    Otherwise, the sqllen value describes the length of the variable in bytes. For example, sqllen is 1280 for a VARCHAR\(1280\) variable.

sqldata
:   A pointer to the memory occupied by this variable. This memory must correspond to the type of the variable and its length.

    The amount of memory required for specific types is returned by the following macros defined in the `sqlca.h` and `sqlda.h` header files.

     DT\_BINARY
     :   \_BINARYSIZE\( n \) returns the amount of storage required to store a BINARY of the specified length.

      DT\_VARCHAR
     :   \_VARCHARSIZE\( n \) returns the amount of storage required to store a VARCHAR of the specified length.

      DT\_DECIMAL
     :   DECIMALSTORAGE\( n \) returns the amount of storage required to store a DECIMAL of the specified length.

      DT\_LONGBINARY
     :   LONGBINARYSIZE\( n \) returns the amount of storage required to store a LONGBINARY of the specified length.

      DT\_LONGNVARCHAR
     :   LONGNVARCHARSIZE\( n \) returns the amount of storage required to store a LONGNVARCHAR of the specified length.

      DT\_LONGVARCHAR
     :   LONGVARCHARSIZE\( n \) returns the amount of storage required to store a LONGVARCHAR of the specified length.

     All other types have fixed storage sizes depending on their type and size. Some examples follow.

    If the type is DT\_INT, then sqldata points to a 32-bit binary integer data value.

    ```
    int ival = (int *)sqlvar->sqldata;
    ```

    If the type is DT\_VARCHAR, then sqldata points to a VARCHAR structure \(which is defined in `sqlca.h`\).

    ```
    typedef struct VARCHAR {
        a_sql_ulen          len;
        char                array[1];
    } VARCHAR;
    
    sqlvar->sqldata = malloc( _VARCHARSIZE( sqlvar->sqllen ) );                  
    VARCHAR *vc = (VARCHAR *)sqlvar->sqldata;
    ```

    DT\_NVARCHAR and DT\_BINARY types have structures similar to DT\_VARCHAR.

    If the type is DT\_LONGVARCHAR, then sqldata points to a LONGVARCHAR structure \(which is defined in `sqlca.h`\).

    ```
    typedef struct LONGVARCHAR {
        a_sql_uint32        array_len;
        a_sql_uint32        stored_len;
        a_sql_uint32        untrunc_len;
        char                array[1];
    } LONGVARCHAR, LONGNVARCHAR, LONGBINARY;
    
    sqlvar->sqldata = malloc( LONGVARCHARSIZE( 128*1024 ) );
    LONGVARCHAR *lvc = (LONGVARCHAR *)sqlvar->sqldata;
    lvc->array_len = 128*1024;
    ```

    DT\_LONGNVARCHAR and DT\_LONGBINARY types have structures similar to DT\_LONGVARCHAR.

    For UPDATE and INSERT statements, this variable is not involved in the operation if the sqldata pointer is a null pointer. For a FETCH, no data is returned if the sqldata pointer is a null pointer. In other words, the column returned by the sqldata pointer is an **unbound column**.

    If the DESCRIBE statement uses LONG NAMES, this field holds the long name of the result set column. If, in addition, the DESCRIBE statement is a DESCRIBE USER TYPES statement, then this field holds the long name of the user-defined data type, instead of the column. If the type is a base type, the field is empty.

sqlind
:   A pointer to the indicator value. An indicator value has type a\_sql\_len. A negative indicator value indicates a NULL value. A positive indicator value indicates that this variable has been truncated by a FETCH statement, and the indicator value contains the length of the data before truncation. A value of -2 indicates a conversion error if the conversion\_error database option is set to Off.

    If the sqlind pointer is the null pointer, no indicator variable pertains to this host variable.

    The sqlind field is also used by the DESCRIBE statement to indicate parameter types. If the type is a user-defined data type, this field is set to DT\_HAS\_USERTYPE\_INFO. In this case, perform a DESCRIBE USER TYPES to obtain information about the user-defined data types.

sqlname
:   A VARCHAR-like structure, as follows:

    ```
    struct sqlname {
       short int  length;
       char       data[ SQL_MAX_NAME_LEN ];
    };
    ```

    It is filled by a DESCRIBE statement and is not otherwise used. This field has a different meaning for the two formats of the DESCRIBE statement:

    SELECT LIST
    :   The name data buffer is filled with the column heading of the corresponding item in the SELECT list.

    BIND VARIABLES
    :   The name data buffer is filled with the name of the host variable that was used as a bind variable, or "?" if an unnamed parameter marker is used.

    On a DESCRIBE SELECT LIST statement, any indicator variables present are filled with a flag indicating whether the SELECT list item is updatable or not. The DT\_UPDATABLE flag and others are defined in the `sqlhosttype.h` header file.

    If the DESCRIBE statement is a DESCRIBE USER TYPES statement, then this field holds the long name of the user-defined data type instead of the column. If the type is a base type, the field is empty.

