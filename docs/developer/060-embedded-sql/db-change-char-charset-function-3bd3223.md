<!-- loio3bd322336c5f1014925a95ca49983826 -->

# db\_change\_char\_charset Function

Change the application's CHAR character set for this connection.



```
unsigned int db_change_char_charset(
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

Data sent and fetched using DT\_FIXCHAR, DT\_VARCHAR, DT\_LONGVARCHAR, and DT\_STRING types are in the CHAR character set.

