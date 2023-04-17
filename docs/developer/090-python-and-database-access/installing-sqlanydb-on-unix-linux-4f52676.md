<!-- loio4f52676bd0d24a999a662769906eb226 -->

# Installing sqlanydb on UNIX/Linux

Set up Python support on UNIX and Linux by running the applicable setup script from the `sdk/python` subdirectory of your software installation.



## Prerequisites

Ensure that Python is installed.



<a name="loio4f52676bd0d24a999a662769906eb226__steps_onp_fcb_dv"/>

## Procedure

1.  Make sure the environment is set up to run the database server.

     Bourne shell and its derivatives
     :   Under Bourne shell and its derivatives, the name of this command is `.` \(a single period\). For example, if data lake Relational Engine is installed in `/opt/iq`, the following statement sources IQ.sh:

        ```
        .  /opt/iq/IQ.sh
        ```

      C-shell and its derivatives
     :   Under C-shell and its derivatives, the command is `source`. For example, if data lake Relational Engine is installed in `/opt/iq`, the following command sources IQ.csh:

        ```
        source  /opt/iq/IQ.csh
        ```

 2.  At a shell prompt, change to the `sdk/python` subdirectory of your software installation.

3.  The package can be installed through the internet or through the package included in your install.

    1.  To install the package over the internet, enter the following command:

        ```
        pip install sqlanydb
        ```

    2.  To install the package included with your install, enter the following command:

        ```
        python setup.py install
        ```


4.  Run the following commands to make a copy of the sample database file in your current directory and test sqlanydb.

    ```
    newdemo
    start_iq iqdemo.db
    python scripts/test.py
    ```

    The test script makes a connection to the database server and executes a SQL query. If the test is successful, then it displays the message `sqlanydb successfully installed.` 

    If the test does not run, then ensure that the `bin64` subdirectory of the software installation is in your path.

    You can delete the sample database and log file from your current directory.




## Results

The sqlanydb module is now ready to use.

