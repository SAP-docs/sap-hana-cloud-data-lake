<!-- loio3be0e92d6c5f1014acc2bbada8add959 -->

# sasql\_store\_result

Transfers the result set from the last query.



```
sasql_result sasql_store_result( sasql_conn <$conn> )
```



## Parameters

 $conn
 :   The connection resource returned by a connect function.

 

## Returns

FALSE if the query does not return a result object, or a result set object, that contains all the rows of the result. The result is cached at the client.



## Remarks

This function is called after executing sasql\_real\_query. After a successful execution of sasql\_real\_query, use sasql\_store\_result to retrieve a handle to the result set returned from the query. The result set handle represents data that has been fetched from the server.

The sasql\_store\_result function caches the result set on the client side. To prevent caching of the result set on the client side, use sasql\_use\_result instead.



## Example

```
<?php
    $conn = sasql_connect( "UID=HDLADMIN;PWD=sql" )
        or die( "Cannot connect to database" );
    if( sasql_real_query( $conn, "SELECT * FROM Customers" ) )
    {
        $num_cols = sasql_field_count( $conn );
        $result = sasql_store_result( $conn );
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

