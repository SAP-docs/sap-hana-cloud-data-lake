<!-- loio3be188fd6c5f10148655c8a94a53281f -->

# Installing sqlanydb on Windows

Set up Python support on Windows by running the applicable setup script from the `SDK\Python` subdirectory of your software installation.



## Prerequisites

Ensure that Python is installed.



## Procedure

1.  At a command prompt with Administrator privilege, change to the `SDK\Python` subdirectory of your software installation.

2.  The package can be installed through the internet or through the package included in your install.

    1.  To install the package over the internet, enter the following command:

        ```
        pip install sqlanydb
        ```

    2.  To install the package included with your install, enter the following command:

        ```
        python setup.py install
        ```


3.  Run the following commands to make a copy of the sample database file in your current directory and test sqlanydb.

    ```
    newdemo
    start_iq iqdemo.db
    python Scripts\test.py
    ```

    The test script makes a connection to the database server and executes a SQL query. If the test is successful, then it displays the message `sqlanydb successfully installed.` 

    If the tests do not run, then ensure that the `bin32` or `bin64` subdirectory of the software installation is in your path.

    You can delete the sample database and log file from your current directory.




## Results

The sqlanydb module is now ready to use.

