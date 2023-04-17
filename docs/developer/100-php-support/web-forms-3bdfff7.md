<!-- loio3bdfff7e6c5f10149588c835118d14c8 -->

# Web Forms

PHP can take user input from a web form, pass it to the database server as a SQL query, and display the result that is returned.

The following example demonstrates a simple web form that gives the user the ability to query the sample database using SQL statements and display the results in an HTML table.

The source code for this sample is contained in your software installation in a file called `webisql.php`.

```
<?php
    echo "<HTML>\n";
    echo "<body onload=\"document.getElementById('qbox').focus()\">\n";

    $qname = $_POST[qname];
    $qname = str_replace( "\\", "", $qname );
    echo "<form method=post action=webisql.php>\n";
    echo "<br>Query : <input id=qbox type=text size=80 name=qname value=\"$qname\">\n";
    echo "<input type=submit>\n";
    echo "</form>\n";
    echo "<HR><br>\n";

    if( ! $qname ) {
        echo "No Current Query\n";
        return;
    }

    $conn = sasql_connect( "UID=HDLADMIN;PWD=sql" );

    if( ! $conn ) {
        echo "sasql_connect failed\n";
    } else {

        $qname = str_replace( "\\", "", $qname );
        $result = sasql_query( $conn, $qname );

        if( ! $result ) {
            echo "sasql_query failed!";
        } else {

            if( sasql_field_count( $conn ) > 0 ) {
                sasql_result_all( $result, "border=1" );
                sasql_free_result( $result );
            } else {
                echo "The statement <h3>$qname></h3> executed successfully!";
            }
        }

        sasql_close( $conn );
    }

    echo "</body>\n";
    echo "</html>\n";
?>
```

This design could be extended to handle complex web forms by formulating customized SQL queries based on the values entered by the user.

