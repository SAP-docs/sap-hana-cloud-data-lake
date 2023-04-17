<!-- loio3bcfe8ed6c5f1014ad21a1eb92a23342 -->

# How to Set Connection Attributes

You use the SQLSetConnectAttr function to control details of the connection. For example, the following statement disables ODBC autocommit.

```
rc = SQLSetConnectAttr( dbc, SQL_ATTR_AUTOCOMMIT, (SQLPOINTER)SQL_AUTOCOMMIT_OFF, 0 );
```

Many aspects of the connection can be controlled through the connection parameters.

