<!-- loio3be1983e6c5f1014891ff37bd8009def -->

# How to Open and Close a Database Connection Using Python

Generally, you open a single connection to a database and then perform all the required operations through it by executing a sequence of SQL statements.

To open a connection, you use the *connect* method. The return value is a handle to the database connection that you use to perform subsequent operations on that connection.

The parameters to the connect method are specified as a series of keyword=value pairs delimited by commas. Keywords are case-insensitive.

```
sqlanydb.connect( keyword=value, ... )
```

Some common connection parameters are as follows:

 DataSourceName="*<dsn\>*"
 :   A short form for this connection parameter is DSN="*<dsn\>*". An example is DataSourceName="SAP IQ 17 Demo".

  UserID="*<user-id\>*"
 :   A short form for this connection parameter is UID="*<user-id\>*". An example is UserID="HDLADMIN".

  Password="*<passwd\>*"
 :   A short form for this connection parameter is PWD="*<passwd\>*". An example is Password="sql".

  DatabaseFile="*<db-file\>*"
 :   A short form for this connection parameter is DBF="*<db-file\>*".

 The following code sample opens and closes a connection to the sample database. You must start the database server with the sample database before running this script.

```
import sqlanydb
myuid = raw_input("Enter your user ID: ")
mypwd = raw_input("Enter your password: ")
# Create a connection object
con = sqlanydb.connect( userid=myuid, password=mypwd )
# Close the connection
con.close()
```

