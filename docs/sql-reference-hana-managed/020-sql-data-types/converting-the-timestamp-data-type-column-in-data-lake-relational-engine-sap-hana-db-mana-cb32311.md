<!-- loiocb32311c9d5942059a9bbfe5acbee22c -->

# Converting the TIMESTAMP Data Type Column in Data Lake Relational Engine \(SAP HANA DB-Managed\)

Convert existing TIMESTAMP data type 6-digits of precision columns to 7 digits of precision:



<a name="loiocb32311c9d5942059a9bbfe5acbee22c__prereq_hjc_tmr_k1c"/>

## Prerequisites

This data lake Relational Engine task can be completed when connected as follows:

-   Connected to SAP HANA database as a SAP HANA database user.

Requires:

-   You have the REMOTE EXECUTE privilege on the remote source *<hana\_relational\_container\_schema\>*\_SOURCE.

You also require one of the following:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the SAP HANA database REMOTE\_EXECUTE procedure associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loiocb32311c9d5942059a9bbfe5acbee22c__context_dsf_5mr_k1c"/>

## Context

The data type of a column cannot be changed. Instead, in the identified table, create a new TIMESTAMP column using 7-digits of precision, copy the data from the original column to the new column, drop the original column, and then rename the new column to that of the original column name. Once migrated, any SAP HANA database virtual tables that point to the data lake Relational Engine table containing the migrated column continue to work.

> ### Caution:  
> Remember that keys, constraints, or indexes associated with a column are lost during conversion. Be sure you have properly documented any associations **before** proceeding so that you can recreated them after migration.



<a name="loiocb32311c9d5942059a9bbfe5acbee22c__steps_kct_5mr_k1c"/>

## Procedure

1.  Verify that the TIMESTAMP\_COLUMNS\_AS\_DATETIMEX database option is enabled. This ensures that newly created TIMESTAMP columns are created with 7-digits of precision.

    ```
    SELECT * FROM REMOTE_EXECUTE_QUERY ('SYSHDL_CONTAINER1_SOURCE', 
       'SELECT connection_property(''TIMESTAMP_COLUMNS_AS_DATETIMEX'')'');
    ```

    1.  If disabled, execute:

        ```
        CALL SYSHDL_CONTAINER1.REMOTE_EXECUTE('SET OPTION PUBLIC.TIMESTAMP_COLUMNS_AS_DATETIMEX = ON');
        ```


2.  Do the following steps once for each column being migrated.

    1.  Add a new column with a TIMESTAMP data type to the table.

        ```
        CALL SYSHDL_CONTAINER1.REMOTE_EXECUTE('ALTER TABLE <table_name> ADD (<new_column_name> TIMESTAMP)');
        ```

    2.  Copy the data from the original column to the new column.

        ```
        CALL SYSHDL_CONTAINER1.REMOTE_EXECUTE('UPDATE <table_name> SET <new_column_name> = <orig_column_name>');
        ```

    3.  Compare the data in the new and original columns to verify the data was successfully copied.

        ```
        CALL SYSHDL_CONTAINER1.REMOTE_EXECUTE('SELECT <orig_column_name>, <new_column_name> FROM <table_name>');
        ```

    4.  Drop the original column from the table.

        ```
        CALL SYSHDL_CONTAINER1.REMOTE_EXECUTE('ALTER TABLE <table_name> DROP <orig_column_name>');
        ```

    5.  \(Optional but recommended\) Rename the new column to that of the original column.

        ```
        CALL SYSHDL_CONTAINER1.REMOTE_EXECUTE('ALTER TABLE <table_name> RENAME <new_column_name> TO <orig_column_name>');
        ```

    6.  Rerun the query that returns all TIMESTAMP data type columns that used 6 digits of precision. Verify that the converted column no longer appears in the result set.

        ```
        SELECT * FROM REMOTE_EXECUTE_QUERY ('SYSHDL_<relational_container_name>_SOURCE', 
           'SELECT t.table_name, c.column_name, u.user_name
              FROM SYSTABCOL c, SYSTAB t, SYSUSER u
              WHERE t.table_id = c.table_id 
                 AND u.user_id = t.creator
                 AND c.domain_id = 13
                 AND t.creator not in (0, 1, 3, 6)');
        ```


3.  Repeat these steps until all columns with 6 digits of precision TIMESTAMP columns in tables identified by the DatalakeHDBCompatibility alert are migrated to 7-digits.


