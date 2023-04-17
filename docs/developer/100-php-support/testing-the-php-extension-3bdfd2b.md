<!-- loio3bdfd2bc6c5f1014a247c87d0aa839ec -->

# Testing the PHP Extension

Perform a quick check to verify that the PHP extension is working correctly.



## Prerequisites

All of the required PHP components should be installed on your system



## Procedure

1.  Make sure that the `bin32` subdirectory of your software installation is in your path. The PHP extension requires the `bin32` directory to be in your path.

2.  At a command prompt, change to the `SDK\PHP\Examples` subdirectory of your software installation. Make sure that the php executable directory is included in your path. Enter the following command:

    ```
    php test.php
    ```

    Messages similar to the following should appear. If the PHP command is not recognized, verify that PHP is in your path.

    ```
    Installation successful
    Using php-5.2.11_sqlanywhere.dll
    Connected successfully
    ```

    If the PHP extension does not load, you can use the command "php -i" for helpful information about your PHP setup. Search for extension\_dir and sqlanywhere in the output from this command.

3.  When you are done, stop the database server by clicking *Shut Down* in the database server messages window.




## Results

The tests should succeed, indicating that the PHP extension is working correctly.

