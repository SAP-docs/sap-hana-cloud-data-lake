<!-- loio3be103176c5f1014a964e48c12c27dfb -->

# sasql\_use\_result

Initiates a result set retrieval for the last query that executed on the connection.



```
sasql_result sasql_use_result( sasql_conn <$conn> )
```



## Parameters

 $conn
 :   The connection resource returned by a connect function.

 

## Returns

FALSE if the query does not return a result object or a result set object. The result is not cached on the client.



## Remarks

This function is called after executing sasql\_real\_query. After a successful execution of sasql\_real\_query, use sasql\_use\_result to retrieve a handle to the result set returned from the query. The result set handle represents data that has not been fetched from the server yet. Each fetch using this result set handle sends a request to the server to retrieve a row of the result set.

The sasql\_use\_result function prevents caching of the result set on the client side. To cache the result set on the client side, use sasql\_store\_result instead.



## Example

```
<?php
    $conn = sasql_connect( "UID=HDLADMIN;PWD=sql" )
        or die( "Cannot connect to database" );
    if( sasql_real_query( $conn, "SELECT * FROM Customers" ) )
    {
        $num_cols = sasql_field_count( $conn );
        $result = sasql_use_result( $conn );
        while( $row = sasql_fetch_row( $result ) )
        {
            $curr_row++;
            $curr_col = 0;
            while( $curr_col < $num_cols ) {
                echo "$row[$curr_col]\t|";
                $curr_col++;
            }
            echo "\n";
        }
        sasql_free_result( $result );
        echo "$curr_row rows.\n";
    }
    sasql_close( $conn );
?>
```

