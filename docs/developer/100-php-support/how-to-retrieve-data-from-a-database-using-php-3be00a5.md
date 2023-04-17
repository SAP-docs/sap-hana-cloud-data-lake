<!-- loio3be00a596c5f10149529814fb0aec4ec -->

# How to Retrieve Data from a Database Using PHP

One use of PHP scripts in web pages is to retrieve and display information contained in a database.



The following examples demonstrate some useful techniques.



## Simple Select Query

The following PHP code demonstrates a convenient way to include the result set of a SELECT statement in a web page. This sample is designed to connect to the sample database and return a list of customers.

This code can be embedded in a web page, provided your web server is configured to execute PHP scripts.

The source code for this sample is contained in your software installation in a file called `query.php`.

```
<?php
  # Connect to the sample database using the default user ID and password HDLADMIN/sql
  $conn = sasql_connect( "UID=HDLADMIN;PWD=<password>" );
  if( ! $conn ) {
      echo "sasql_connect failed\n";
  } else {
      echo "Connected successfully\n";
      # Execute a SELECT statement
      $result = sasql_query( $conn, "SELECT * FROM Customers" );
      if( ! $result ) {
          echo "sasql_query failed!";
      } else {
          echo "query completed successfully\n";
          # Generate HTML from the result set
          sasql_result_all( $result );
          sasql_free_result( $result );
      }
      sasql_close( $conn );
  }
?>
```

The sasql\_result\_all function fetches all the rows of the result set and generates an HTML output table to display them. The sasql\_free\_result function releases the resources used to store the result set.



## Fetching by Column Name

In certain cases, you do not want to display all the data from a result set, or you want to display the data in a different manner. The following sample illustrates how you can exercise greater control over the output format of the result set. PHP allows you to display as much information as you want in whatever manner you choose.

The source code for this sample is contained in your software installation in a file called `fetch.php`.

```
<?php
  # Connect to the sample database using the user ID and password HDLADMIN/sql
  $conn = sasql_connect( "UID=HDLADMIN;PWD=<password>" );
  if( ! $conn ) {
      die ("Connection failed");
  } else {
      # Connected successfully.
  }
  # Execute a SELECT statement
  $result = sasql_query( $conn, "SELECT * FROM Customers" );
  if( ! $result ) {
      echo "sasql_query failed!";
      return 0;
  } else {
      echo "query completed successfully\n";
  }
  # Retrieve meta information about the results
  $num_cols = sasql_num_fields( $result );
  $num_rows = sasql_num_rows( $result );
  echo "Num of rows = $num_rows\n";
  echo "Num of cols = $num_cols\n";
  while( ($field = sasql_fetch_field( $result )) ) {
      echo "Field # : $field->id \n";  
      echo "\tname   : $field->name \n";  
      echo "\tlength : $field->length \n";   
      echo "\ttype   : $field->type \n";  
  }
  # Fetch all the rows
  $curr_row = 0;
  while( ($row = sasql_fetch_row( $result )) ) {
      $curr_row++;
      $curr_col = 0;
      while( $curr_col < $num_cols ) {
          echo "$row[$curr_col]\t|"; 
          $curr_col++;
      }
      echo "\n";
  }
  # Clean up.
  sasql_free_result( $result );
  sasql_disconnect( $conn );
?>
```

The sasql\_fetch\_array function returns a single row from the table. The data can be retrieved by column names and column indexes.

The sasql\_fetch\_assoc function returns a single row from the table as an associative array. The data can be retrieved by using the column names as indexes. The following is an example.

The source code for this sample is contained in your software installation in a file called `fetch_assoc.php`.

```
<?php
  # Connect to the sample database using the user ID and password HDLADMIN/sql
  $conn = sasql_connect("UID=HDLADMIN;PWD=<password>");
  
  /* check connection */
  if( sasql_errorcode() ) {
      printf("Connect failed: %s\n", sasql_error());
      exit();
  }
  
  $query = "SELECT Surname, Phone FROM Employees ORDER by EmployeeID";
  
  if( $result = sasql_query($conn, $query) ) {
  
      /* fetch associative array */
      while( $row = sasql_fetch_assoc($result) ) {
          printf ("%s (%s)\n", $row["Surname"], $row["Phone"]);
      }
  
      /* free result set */
      sasql_free_result($result);
  }
  
  /* close connection */
  sasql_close($conn);
?>
```

Two other similar methods are provided in the PHP interface: sasql\_fetch\_row returns a row that can be searched by column indexes only, while sasql\_fetch\_object returns a row that can be searched by column names only.

For an example of the sasql\_fetch\_object function, see the `fetch_object.php` example script.



## Nested Result Sets

When a SELECT statement is sent to the database, a result set is returned. The sasql\_fetch\_row and sasql\_fetch\_array functions retrieve data from the individual rows of a result set, returning each row as an array of columns that can be queried further.

The source code for this sample is contained in your software installation in a file called `nested.php`.

```
<?php
  $conn = sasql_connect( "UID=HDLADMIN;PWD=<password>" );
  if( $conn ) {
      // get the GROUPO user id
      $result = sasql_query( $conn, 
            "SELECT user_id FROM SYS.SYSUSER " .
            "WHERE user_name='GROUPO'" );
      if( $result ) {
          $row = sasql_fetch_array( $result );
          $user = $row[0];
      } else {
          $user = 0;
      }
      // get the tables created by user GROUPO
      $result = sasql_query( $conn, 
            "SELECT table_id, table_name FROM SYS.SYSTABLE " .
            "WHERE creator = $user" );
      if( $result ) {
          $num_rows = sasql_num_rows( $result );
          echo "Returned rows : $num_rows\n";
          while( $row = sasql_fetch_array( $result ) ) {
              echo "Table: $row[1]\n";
              $query = "SELECT table_id, column_name FROM SYS.SYSCOLUMN " .
                        "WHERE table_id = '$row[table_id]'";
              $result2 = sasql_query( $conn, $query );
              if( $result2 ) {
                  echo "Columns:";
                  while( $detailed = sasql_fetch_array( $result2 ) ) {
                      echo " $detailed[column_name]";
                  }
                  sasql_free_result( $result2 );
              }
              echo "\n\n";
          }
          sasql_free_result( $result );
      }
      sasql_disconnect( $conn );
  }
?>
```

In the above sample, the SQL statement selects the table ID and name for each table from SYSTAB. The sasql\_query function returns an array of rows. The script iterates through the rows using the sasql\_fetch\_array function to retrieve the rows from an array. An inner iteration goes through the columns of each row and prints their values.

