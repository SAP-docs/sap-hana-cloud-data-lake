<!-- loio3bd5b17c6c5f1014945fd2b7ec7cba6a -->

# Data Lake Relational Engine JDBC Driver Connection Strings

To connect to a database using the data lake Relational Engine JDBC driver, supply a URL for the database.

The following is an example of how to connect to a database.

```
Connection con = DriverManager.getConnection( "jdbc:sqlanywhere:DSN=myDataLakeInstance;Password=XXXXXXXXX");
```

The URL contains jdbc:sqlanywhere: followed by a connection string. If the `sajdbc4.jar` file is in your class file path, then the data lake Relational Engine JDBC driver is loaded automatically and handles the URL. As shown in the example, an ODBC data source \(DSN\) may be specified for convenience, but you can also use explicit connection parameters, separated by semicolons, in addition to or instead of the data source connection parameter.

If you do not use a data source, you must specify all required connection parameters in the connection string:

```
Connection con = DriverManager.getConnection( "jdbc:sqlanywhere:UserID=XXXXXXX;Password=XXXXXXXXX;ENC=TLS(direct=yes);HOST=<HDL-endpoint-for-instance>:443" );
```

The Driver connection parameter is not required since neither the ODBC driver nor ODBC driver manager is used. If present, it is ignored.

