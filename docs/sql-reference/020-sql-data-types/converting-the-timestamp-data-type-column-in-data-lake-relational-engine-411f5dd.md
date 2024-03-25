<!-- loio411f5dda79e949f4a13c913783ce3691 -->

# Converting the TIMESTAMP Data Type Column in Data Lake Relational Engine

Convert existing TIMESTAMP data type 6-digits of precision columns to 7 digits of precision:



<a name="loio411f5dda79e949f4a13c913783ce3691__converting_column_prereq1"/>

## Prerequisites

This data lake Relational Engine task can be completed when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.

Requires one of the following:

-   You own the table being migrated
-   SELECT ANY TABLE and ALTER ANY TABLE system privileges
-   SELECT, ALTER, and UPDATE object-level privilege on the table
-   SELECT, ALTER, and UPDATE object-level privilege on the schema containing the table if the schema is owned by another user



<a name="loio411f5dda79e949f4a13c913783ce3691__converting_column_context1"/>

## Context

The data type of a column cannot be changed. Instead, in the identified table, create a new TIMESTAMP column using 7-digits of precision, copy the data from the original column to the new column, drop the original column, and then rename the new column to that of the original column name. Once migrated, any SAP HANA database virtual tables that point to the data lake Relational Engine table containing the migrated column continue to work.

> ### Caution:  
> Remember that keys, constraints,comments, grants, or indexes associated with a column are lost during conversion. Be sure you have properly documented any associations **before** proceeding so that you can recreated them after migration.



<a name="loio411f5dda79e949f4a13c913783ce3691__converting_column_steps1"/>

## Procedure

1.  Verify that the TIMESTAMP\_COLUMNS\_AS\_DATETIMEX database option is enabled. This ensures that newly created TIMESTAMP columns are created with 7-digits of precision.

    ```
    SELECT connection_property('TIMESTAMP_COLUMNS_AS_DATETIMEX');
    ```

    1.  If disabled, execute:

        ```
        SET OPTION PUBLIC.TIMESTAMP_COLUMNS_AS_DATETIMEX = ON;
        ```


2.  Do the following steps once for each column being migrated.

    1.  Add a new column with a TIMESTAMP data type to the table.

        ```
        ALTER TABLE <table_name> ADD (<new_column_name> TIMESTAMP);
        ```

    2.  Copy the data from the original column to the new column.

        ```
        UPDATE <table_name> SET <new_column_name> = <orig_column_name>;
        ```

    3.  Compare the data in the new and original columns to verify the data was successfully copied.

        ```
        SELECT <orig_column_name>, <new_column_name> FROM <table_name>;
        ```

    4.  Drop the original column from the table.

        ```
        ALTER TABLE <table_name> DROP <orig_column_name>;
        ```

    5.  \(Optional but recommended\) Rename the new column to that of the original column.

        ```
        ALTER TABLE <table_name> RENAME <new_column_name> TO <orig_column_name>;
        ```

    6.  Rerun the query that returns all TIMESTAMP data type columns that used 6 digits of precision. Verify that the converted column no longer appears in the result set.

        ```
        SELECT t.table_name, c.column_name, u.user_name
           FROM SYSTABCOL c, SYSTAB t, SYSUSER u
           WHERE t.table_id = c.table_id 
              AND u.user_id = t.creator
              AND c.domain_id = 13
              AND t.creator not in (0, 1, 3, 6);
        ```


3.  Repeat these steps until all columns with 6 digits of precision TIMESTAMP columns in tables identified by the DatalakeHDBCompatibility alert are migrated to 7-digits.




<a name="loio411f5dda79e949f4a13c913783ce3691__identifying_columns_whats_next"/>

## Next Steps

Once any columns are converted, you need to recreate any keys, constraints, comments,grants, or indexes associated with the original columns. See [Rebuilding Column Keys, Constraints, Comments, Grants, or Indexes on TIMESTAMP Data Type Columns in Data Lake Relational Engine](rebuilding-column-keys-constraints-comments-grants-or-indexes-on-timestamp-data-type-colu-fd5cb63.md).

