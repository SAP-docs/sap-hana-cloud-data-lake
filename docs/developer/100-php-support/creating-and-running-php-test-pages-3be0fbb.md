<!-- loio3be0fbb96c5f1014ba89969f61018734 -->

# Creating and Running PHP Test Pages

Create and run several web pages that test whether PHP is set up properly.



## Prerequisites

You must install PHP.



## Context

This procedure applies to all configurations.



## Procedure

1.  Create a file in your root web content directory named `info.php`.

    If you are not sure which directory to use, then check your web server's configuration file. In Apache installations, the content directory is often called `htdocs`.

2.  Insert the following code into this file:

    ```
    <?php phpinfo(); ?>
    ```

    The PHP function, phpinfo, generates a page of system setup information. This confirms that your installation of PHP and your web server are working together properly.

3.  Copy the file `connect.php` from the `sdk\php\examples` directory to your root web content directory. This confirms that your installation of PHP, the PHP extension, and the database server are working together properly.

4.  Create a file in your root web content directory named `sa_test.php` and insert the following code into this file:

    ```
    <?php
      $conn = sasql_connect( "UID=HDLADMIN;PWD=<password>" );
      $result = sasql_query( $conn, "SELECT * FROM Employees" );
      sasql_result_all( $result );
      sasql_free_result( $result );
      sasql_disconnect( $conn );
    ?>
    ```

    The sa\_test page displays the contents of the Employees table.

5.  Start your web server if it is required.

    For example, to start the Apache web server, run the following command from the `bin` subdirectory of your Apache installation:

    ```
    apachectl start
    ```

6.  Make sure the environment is set up to run the database server. Depending on which shell you are using, enter the appropriate command to source the SQL Anywhere configuration script from the software installation directory:

     Bourne shell and its derivatives
     :   Under Bourne shell and its derivatives, the name of this command is `.` \(a single period\). For example, if data lake Relational Engine is installed in <code><i>/opt/sqlanywhere17</i></code>, the following statement sources `sa_config.sh` \(use `bin32` for 32-bit environments\):

        ```
        .  /opt/sqlanywhere17/bin64/sa_config.sh
        ```

        For example, on a macOS system, run the following command to source `sa_config.sh`:

        ```
        . /Applications/SQLAnywhere17/System/bin64/sa_config.sh
        ```

      C-shell and its derivatives
     :   Under C-shell and its derivatives, the command is `source`. For example, if data lake Relational Engine is installed in <code><i>/opt/sqlanywhere17</i></code>, the following command sources `sa_config.csh` \(use `bin32` for 32-bit environments\):

        ```
        source  /opt/sqlanywhere17/bin64/sa_config.csh
        ```

 7.  To test that PHP and your web server are working correctly with the database server, access the test pages from a browser that is running on the same computer as the server:


    <table>
    <tr>
    <th valign="top">

    Test Page


    
    </th>
    <th valign="top">

    URL


    
    </th>
    </tr>
    <tr>
    <td valign="top">

     `info.php` 


    
    </td>
    <td valign="top">

    ```
    http://localhost/info.php
    ```


    
    </td>
    </tr>
    <tr>
    <td valign="top">

     `connect.php` 


    
    </td>
    <td valign="top">

    ```
    http://localhost/connect.php
    ```


    
    </td>
    </tr>
    <tr>
    <td valign="top">

     `sa_test.php` 


    
    </td>
    <td valign="top">

    ```
    http://localhost/sa_test.php
    ```


    
    </td>
    </tr>
    </table>
    



## Results

The info page displays the output from the `phpinfo()` call.

The connect page displays the message `Connected successfully`.

The sa\_test page displays the contents of the Employees table.

