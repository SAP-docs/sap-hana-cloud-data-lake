<!-- loioa629925c84f21015bce6c0ceb1fa594c -->

# Current Option Settings

You can obtain a list of option settings, or the values of individual options, using `sp_iqcheckoptions`, `sa_conn_properties`, the `SET` statement, and the `SYSOPTIONS` system view.

-   For the connected user, the `sp_iqcheckoptions` stored procedure displays a list of the current value and the default value of database options that have been changed from the default. `sp_iqcheckoptions` considers all data lake Relational Engine and SAP SQL Anywhere database options. Data lake Relational Engine modifies some SAP SQL Anywhere option defaults, and these modified values become the new default values. Unless the new data lake Relational Engine default value is changed again, `sp_iqcheckoptions` does not list the option.

    `sp_iqcheckoptions` also lists server start-up options that have been changed from the default values.

    When a DBA runs `sp_iqcheckoptions`, he or she sees all options set on a permanent basis for all roles and users and sees temporary options set for DBA. Users who are not DBAs see their own temporary options. All users see nondefault server start-up options.

    The `sp_iqcheckoptions` stored procedure requires no parameters. In Interactive SQL, run:

    ```
    sp_iqcheckoptions
    ```

    The system table `DBA.SYSOPTIONDEFAULTS` contains all of the names and default values of the data lake Relational Engine and SAP SQL Anywhere options. You can query this table to see all option default values.

-   Current option settings for your connection are available as a subset of connection properties. You can list all connection properties using the `sa_conn_properties` system procedure:

    ```
    call sa_conn_properties
    ```

-   In Interactive SQL, the `SET` statement with no arguments lists the current setting of options:

    ```
    SET
    ```

-   Query the `SYSOPTIONS` system view:

    ```
    SELECT *
    FROM SYSOPTIONS
    ```

    This shows all `PUBLIC` values, and those `USER` values that have been explicitly set.

-   Use the `connection_property` system function to obtain an individual option setting. For example, this statement returns the value of the Ansinull option:

    ```
    SELECT connection_property ('Ansinull')
    ```


