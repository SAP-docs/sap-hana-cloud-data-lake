<!-- loio3bd32a2b6c5f10148695865854b9f071 -->

# db\_change\_nchar\_charset Function

Change the application's NCHAR character set for this connection.



```
unsigned int db_change_nchar_charset(
SQLCA * <sqlca>,
char * charset );
```



## Parameters

 sqlca
 :   A pointer to a SQLCA structure.

  charset
 :   A string representing the character set.

 

## Returns

1 if the change is successful; 0 otherwise.



## Remarks

Data sent and fetched using DT\_NFIXCHAR, DT\_NVARCHAR, DT\_LONGNVARCHAR, and DT\_NSTRING host variable types are in the NCHAR character set.

If the db\_change\_nchar\_charset function is not called, all data is sent and fetched using the CHAR character set. Typically, an application that wants to send and fetch Unicode data should set the NCHAR character set to UTF-8.

If this function is called, the charset parameter is usually "UTF-8". The NCHAR character set cannot be set to UTF-16.

In Embedded SQL, NCHAR, NVARCHAR and LONG NVARCHAR are described as DT\_FIXCHAR, DT\_VARCHAR, and DT\_LONGVARCHAR, respectively, by default. If the db\_change\_nchar\_charset function has been called, these types are described as DT\_NFIXCHAR, DT\_NVARCHAR, and DT\_LONGNVARCHAR, respectively.

