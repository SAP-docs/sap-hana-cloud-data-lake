<!-- loio3bda5df06c5f1014bda2e294745f9008 -->

# Building the PHP Extension on UNIX/Linux

You can build the PHP extension using the steps described here.



## Prerequisites

The following is a list of software you must have on your system to build the PHP extension on UNIX/Linux:

-   The data lake Relational Engine PHP extension source code. This code is included in the data lake Relational Engine software install under `sdk/php`.

-   The PHP development package \(php5-dev\) which can be downloaded and installed from the PHP web site.




## Context

You must have the same access privileges as the person who installed PHP to perform certain steps of the installation. Most UNIX and Linux systems offer a *sudo* command that allows users with insufficient permissions to execute certain commands as a user with the right to execute them.



## Procedure

1.  Source the data lake Relational Engine environment variables using one of the supplied scripts.

     Bourne shell and its derivatives
     :   Under Bourne shell and its derivatives, the name of this command is `.` \(a single period\). For example, if data lake Relational Engine is installed in <code><i>/opt/sqlanywhere17</i></code>, the following statement sources `sa_config.sh` \(use `bin32` for 32-bit environments\):

        ```
        .  /opt/sqlanywhere17/bin64/sa_config.sh
        ```

        For example, on a Mac, run the following command to source `sa_config.sh`:

        ```
        . /Applications/SQLAnywhere17/System/bin64/sa_config.sh
        ```

      C-shell and its derivatives
     :   Under C-shell and its derivatives, the command is `source`. For example, if data lake Relational Engine is installed in <code><i>/opt/sqlanywhere17</i></code>, the following command sources `sa_config.csh` \(use `bin32` for 32-bit environments\):

        ```
        source  /opt/sqlanywhere17/bin64/sa_config.csh
        ```

 2.  Change to the data lake Relational Engine `sdk/php` directory containing the data lake Relational Engine PHP extension software.

3.  Build the extension using the following commands:

    ```
    $ phpize
    $ ./configure --with-sqlanywhere
    $ make
    $ make test
    $ sudo make install
    ```

4.  Edit the `php.ini` file in your PHP software install directory and make sure that the `enable_dl` option is enabled as follows.

    ```
    enable_dl = On
    ```

5.  Verify that PHP is aware of the extension by listing the contents of the PHP extensions directory and looking for `sqlanywhere.so`.

    ```
    $ php -i | grep extension_dir
    $ ls <extension_dir>
    ```




## Results

If you are unsuccessful in building the PHP extension, keep track of the output of these commands and post it to the SQL Anywhere Forum for assistance.

