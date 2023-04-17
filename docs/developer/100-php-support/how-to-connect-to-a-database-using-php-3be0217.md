<!-- loio3be0217e6c5f1014bbcafda7ad2bfae1 -->

# How to Connect to a Database Using PHP

To make a connection to a database, pass a standard database connection string to the database server as a parameter to the sasql\_connect function.

The <?php and ?\> tags tell the web server that it should let PHP execute the code that lies between them and replace it with the PHP output.

The source code for this example is contained in your software installation in a file called `connect.php`.

```
<?php
  # Connect to the sample database 
  $conn = sasql_connect( "UID=HDLADMIN;PWD=<password>" );
  if( ! $conn ) {
      echo "Connection failed\n";
  } else {
      echo "Connected successfully\n";
      sasql_close( $conn );
  }?>
```

This script attempts to make a connection to a database on a local server. For this code to succeed, the sample database or one with identical credentials must be started on a local server.

