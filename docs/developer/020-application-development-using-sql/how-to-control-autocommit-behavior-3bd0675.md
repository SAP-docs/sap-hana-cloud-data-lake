<!-- loio3bd067536c5f10148c86d9589b7e4302 -->

# How to Control Autocommit Behavior

The way to control the commit behavior of your application depends on the programming interface you are using. The implementation of autocommit may be client-side or server-side, depending on the interface.



## Control Autocommit Mode \(ADO.NET\)

By default, the ADO.NET data provider operates in autocommit mode. To use explicit transactions, use the SAConnection.BeginTransaction method. Automatic commit is handled on the client side by the provider.



## Control Autocommit Mode \(Embedded SQL\)

By default, Embedded SQL applications operate in manual commit mode. To enable automatic commits temporarily, set the auto\_commit database option \(a server-side option\) to On using a statement such as the following:

```
SET TEMPORARY OPTION auto_commit='On'
```



## Control Autocommit Mode \(JDBC\)

By default, JDBC operates in autocommit mode. To turn off autocommit, use the setAutoCommit method of the connection object:

```
conn.setAutoCommit( false );
```



## Control Autocommit Mode \(ODBC\)

By default, ODBC operates in autocommit mode. The way you turn off autocommit depends on whether you are using ODBC directly, or using an application development tool. If you are programming directly to the ODBC interface, set the SQL\_ATTR\_AUTOCOMMIT connection attribute. The following example disables autocommit.

```
SQLSetConnectAttr( hdbc, SQL_ATTR_AUTOCOMMIT, (SQLPOINTER)SQL_AUTOCOMMIT_OFF, 0 );
```



## Control Autocommit Mode \(OLE DB\)

By default, the OLE DB provider operates in autocommit mode. To use explicit transactions, use the ITransactionLocal::StartTransaction, ITransaction::Commit, and ITransaction::Abort methods.



## Control Autocommit Mode \(Open Client\)

By default, a connection made through Open Client operates in autocommit mode. You can change this behavior by setting the chained database option \(a server-side option\) to On in your application using a statement such as the following:

```
SET OPTION chained='On'
```



## Control Autocommit Mode \(Perl\)

By default, Perl operates in autocommit mode. To disable autocommit, set the AutoCommit option:

```
my $dbh = DBI->connect( "DBI:SQLAnywhere:$connstr", '', '', {AutoCommit => 0} );
```



## Control Autocommit Mode \(PHP\)

By default, PHP operates in autocommit mode. To disable autocommit, use the sasql\_set\_option function:

```
$result = sasql_set_option( $conn, "auto_commit", "Off" );
```



## Control Autocommit Mode \(Python\)

By default, Python operates in manual commit mode. To enable autocommit, set the auto\_commit database option \(a server-side option\) to On using a statement such as the following:

```
cursor.execute("SET TEMPORARY OPTION auto_commit='On'")
```



## Control Aautocommit Mode \(Ruby\)

By default, Ruby operates in manual commit mode. To enable autocommit, set the auto\_commit database option \(a server-side option\) to On using a statement such as the following:

```
rc = api.sqlany_execute_immediate( conn, "SET TEMPORARY OPTION auto_commit='On'" )
```



## Control Autocommit Mode \(on the server\)

By default, the database server operates in manual commit mode. To enable automatic commits temporarily, set the auto\_commit database option \(a server-side option\) to On using a statement such as the following:

```
SET TEMPORARY OPTION auto_commit='On'
```

> ### Note:  
> Do not set the auto\_commit server option directly when using an API such as ADO.NET, JDBC, ODBC, or OLE DB. Use the API-specific mechanism for enabling or disabling automatic commit. For example, in ODBC set the SQL\_ATTR\_AUTOCOMMIT connection attribute using SQLSetConnectAttr. When you use the API, the driver can track the current setting of automatic commit.

> ### Note:  
> The auto\_commit option cannot be set in Interactive SQL using a SET TEMPORARY OPTION statement since this sets the Interactive SQL option of the same name. You could imbed the statement in an EXECUTE IMMEDIATE statement, however it is inadvisable to do so as unpredictable behavior can result. By default, Interactive SQL operates in manual commit mode \(auto\_commit = 'Off'\).

