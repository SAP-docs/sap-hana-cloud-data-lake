<!-- loio520ce6c6c90f47769eb2f1ddafa8bf49 -->

# Decimal Precision of the TIMESTAMP Data Type in Data Lake Relational Engine

Decimal precision for TIMESTAMP data type columns is controlled by the TIMESTAMP\_COLUMNS\_AS\_DATETIMEX database option.



This option controls whether TIMESTAMP data type columns in data lake Relational Engine support 6 or 7 decimal precision.

When set to ON, **new** TIMESTAMP data type columns use 7 decimal precision. When set to OFF, **new** TIMESTAMP data type columns use 6 decimal precision. This option has **no impact** on the precision of **existing** TIMESTAMP columns; they **retain** their original precision of 6 decimals regardless of the options current setting. Only new TIMESTAMP columns created after the database option is enabled use the new default of 7 decimal precision.

Precision conflicts between TIMESTAMP data types result in data loss. For example, the TIMESTAMP data type in SAP HANA database uses 7 decimal precision. If you import this data into a data lake Relational Engine column configured to use 6 decimal precision, the last digit of the source data is truncated.

> ### Caution:  
> Once data is truncated during import, the truncated data cannot be recovered. Enabling the TIMESTAMP\_COLUMNS\_AS\_DATETIMEX database option does **not** recover the truncated data.

If you plan to import 7 decimal precision data into existing 6 decimal precision data lake Relational Engine columns, then to avoid data loss, you should first ensure that the TIMESTAMP\_COLUMNS\_AS\_DATETIMEX database option is enabled and then migrate the relevant existing data lake Relational Engine TIMESTAMP data type columns using 6 decimal precision to 7 decimal precision **before** importing any the data.

> ### Caution:  
> Migrating the columns will not recover the truncated data, but it **will** prevent future truncations during data imports.

To identify existing tables with TIMESTAMP columns using 6 decimal precision, run the following query:

```
SELECT t.table_name, c.column_name 
   FROM SYSTABCOL c, SYSTAB t
   WHERE t.table_id = c.table_id 
      AND c.domain_id = 13
      AND t.creator not in (0, 1, 3, 6)

 
```

To identify existing tables with TIMESTAMP columns using 7 decimal precision \(DATETIMEX\), run the following query:

```
SELECT t.table_name, c.column_name 
   FROM SYSTABCOL c, SYSTAB t
   WHERE t.table_id = c.table_id 
      AND c.domain_id = 41
      AND t.creator not in (0, 1, 3, 6)

 
```

To migrate existing TIMESTAMP data type columns to use 7 decimal precision:

1.  Ensure the TIMESTAMP\_COLUMNS\_AS\_DATETIMEX database option set to ON.
2.  Create a new column in the table using the TIMESTAMP data type.
3.  Use the UPDATE statement to copy data from the original column to the new column.
4.  Drop the original column.
5.  Rename the new column to that of the original column.

If enabling the TIMESTAMP\_COLUMNS\_AS\_DATETIMEX database option is not feasible in your instance, but data loss due to truncation during import is an issue, migrate TIMESTAMP data type columns to use DATETIMEX data type. The DATETIMEX data type uses 7 decimal precision regardless of the TIMESTAMP\_COLUMNS\_AS\_DATETIMEX setting. No data loss due to truncation occurs during an import.

**Related Information**  


[TIMESTAMP\_COLUMNS\_AS\_DATETIMEX Option for Data Lake Relational Engine](../090-database-options/timestamp-columns-as-datetimex-option-for-data-lake-relational-engine-082fdf9.md "Controls whether DATETIMEX data type columns are automatically created when TIMESTAMPS data type columns are requested.")

[Decimal Precision of the TIMESTAMP Data Type in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/5cbca14157bc452c88126325667e4342.html "Decimal precision for TIMESTAMP data type columns is controlled by the TIMESTAMP_COLUMNS_AS_DATETIMEX database option.") :arrow_upper_right:

