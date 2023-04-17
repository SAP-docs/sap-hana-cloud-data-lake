<!-- loio3bd106406c5f101493c5af0261d4eb1c -->

# db\_get\_property Function

Obtain information about the database interface or the server to which you are connected.



```
unsigned int db_get_property(
SQLCA * <sqlca>,
a_db_property <property>,
char * <value_buffer>,
int <value_buffer_size> );
```



## Parameters

 sqlca
 :   A pointer to a SQLCA structure.

  a\_db\_property
 :   The property requested, either DB\_PROP\_CLIENT\_CHARSET, DB\_PROP\_SERVER\_ADDRESS, or DB\_PROP\_DBLIB\_VERSION.

  value\_buffer
 :   This argument is filled with the property value as a null-terminated string.

  value\_buffer\_size
 :   The maximum length of the string value\_buffer, including room for the terminating null character.

 

## Returns

1 if successful; 0 otherwise.



## Remarks

This function is used to obtain information about the database interface or the server to which you are connected.

The following properties are supported:

 DB\_PROP\_CLIENT\_CHARSET
 :   This property value gets the client character set \(for example, "windows-1252"\).

  DB\_PROP\_SERVER\_ADDRESS
 :   This property value gets the current connection's server network address as a printable string. The shared memory protocol always returns the empty string for the address. The TCP/IP protocol returns non-empty string addresses.

  DB\_PROP\_DBLIB\_VERSION
 :   This property value gets the database interface library's version \(for example, "17.0.11.1293"\).

 