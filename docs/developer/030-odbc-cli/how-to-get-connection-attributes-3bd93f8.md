<!-- loio3bd93f8d6c5f101482c3bc193364c8a9 -->

# How to Get Connection Attributes

You use the SQLGetConnectAttr function to get details of the connection. For example, the following statement returns the connection state.

```
rc = SQLGetConnectAttr( dbc, SQL_ATTR_CONNECTION_DEAD,
   (SQLPOINTER)&closed, SQL_IS_INTEGER, 0 );
```

When using the SQLGetConnectAttr function to get the SQL\_ATTR\_CONNECTION\_DEAD attribute, the value SQL\_CD\_TRUE is returned if the connection has been dropped even if no request has been sent to the server since the connection was dropped. Determining if the connection has been dropped is done without making a request to the server, and the dropped connection is detected within a few seconds. The connection can be dropped for several reasons, such as an idle timeout.

