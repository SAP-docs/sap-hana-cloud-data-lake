<!-- loio3bf6a9c06c5f1014b7ffe7b6eaccffab -->

# sqlany\_register\_callback\(a\_sqlany\_connection \*, a\_sqlany\_callback\_type, SQLANY\_CALLBACK\_PARM\) Method

Register a callback routine.



```
public sacapi_bool sqlany_register_callback (
    a_sqlany_connection * sqlany_conn,
    a_sqlany_callback_type index,
    SQLANY_CALLBACK_PARM callback
)
```



## Parameters

sqlany\_conn
:   A connection object with a connection established using sqlany\_connect\(\).

index
:   Any of the callback types listed below.

callback
:   Address of the callback routine.



## Returns

1 when successful or 0 when unsuccessful.



## Remarks

This function can be used to register callback functions.

```
A callback type can be any one of the following: 
   CALLBACK_START
   CALLBACK_WAIT
   CALLBACK_FINISH
   CALLBACK_MESSAGE
   CALLBACK_CONN_DROPPED
   CALLBACK_DEBUG_MESSAGE
   CALLBACK_VALIDATE_FILE_TRANSFER


The following example shows a simple message callback routine and how to register it. 
void SQLANY_CALLBACK messages(
   a_sqlany_connection *sqlany_conn,
   a_sqlany_message_type msg_type,
   int sqlcode,
   unsigned short length,
   char *msg )
{
   size_t  mlen;
   char    mbuffer[80];

   mlen = __min( length, sizeof(mbuffer) );
   strncpy( mbuffer, msg, mlen );
   mbuffer[mlen] = '\0';
   printf( "Message is \"s".
", mbuffer );
   sqlany_sqlstate( sqlany_conn, mbuffer, sizeof( mbuffer ) );
   printf( "SQLCode(%d) SQLState(\"s")

", sqlcode, mbuffer );
}
```

