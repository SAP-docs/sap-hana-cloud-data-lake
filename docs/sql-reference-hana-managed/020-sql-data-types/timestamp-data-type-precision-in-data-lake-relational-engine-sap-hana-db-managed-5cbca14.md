<!-- loio5cbca14157bc452c88126325667e4342 -->

# TIMESTAMP Data Type Precision in Data Lake Relational Engine \(SAP HANA DB-Managed\)

Precision conflicts between TIMESTAMP data types result in data loss.





### 

The TIMESTAMP data type in SAP HANA database uses 7-digits of precision. The TIMESTAMP data type in data lake Relational Engine uses 6 or 7-digits of precision. If you import 7-digits of data into 6-digits of precision columns, then the last digit of the data source is truncated resulting in data loss. To avoid losing data, the data lake Relational Engine columns need to be created as 7-digits of precision columns prior to importing the 7-digits of precision data.

Precision for TIMESTAMP data type columns is controlled by the TIMESTAMP\_COLUMNS\_AS\_DATETIMEX database option. This option controls whether TIMESTAMP data type columns in data lake Relational Engine support 6 or 7-digits of precision.

When set to ON, **new** TIMESTAMP data type columns use 7-digits of precision. When set to OFF, **new** TIMESTAMP data type columns use 6-digits of precision. Once set, this option has **no impact** on the precision of **existing** TIMESTAMP columns; they **retain** their original precision. Only new TIMESTAMP columns created after the database option is enabled use the new default of 7-digits.

The default for the TIMESTAMP\_COLUMNS\_AS\_DATETIMEX database option depends on when your instance was created. See [TIMESTAMP\_COLUMNS\_AS\_DATETIMEX Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../040-database-options/timestamp-columns-as-datetimex-option-for-data-lake-relational-engine-sap-hana-db-managed-34e3540.md).

> ### Caution:  
> Once data is truncated, the truncated data cannot be recovered. Enabling the TIMESTAMP\_COLUMNS\_AS\_DATETIMEX database option does **not** recover the truncated data. Migrating the columns will not recover the truncated data, but **will** prevent future truncations during future data loads.

**Related Information**  


[CAST Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../050-system-sql-functions/cast-function-for-data-lake-relational-engine-sap-hana-db-managed-4a2c75b.md "Returns the value of an expression converted to a supplied data type.")

[UPDATE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/update-statement-for-data-lake-relational-engine-sap-hana-db-managed-2de4f7a.md "Modifies existing rows of a single table, or a view that contains only one table.")

[INSERT Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/insert-statement-for-data-lake-relational-engine-sap-hana-db-managed-cbe6857.md "Inserts a single row or a selection of rows, from elsewhere in the current database, into the table. This command can also insert a selection of rows from another database into the table.")

[TIMESTAMP\_COLUMNS\_AS\_DATETIMEX Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../040-database-options/timestamp-columns-as-datetimex-option-for-data-lake-relational-engine-sap-hana-db-managed-34e3540.md "Controls whether DATETIMEX data type columns are automatically created when TIMESTAMPS data type columns are requested.")

[TIMESTAMP Data Type Precision in Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/520ce6c6c90f47769eb2f1ddafa8bf49.html "Precision conflicts between TIMESTAMP data types result in data loss.") :arrow_upper_right:

[TIMESTAMP\_RTRUNCATION Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../040-database-options/timestamp-rtruncation-option-for-data-lake-relational-engine-sap-hana-db-managed-7ea796c.md "Controls whether INSERT, UPDATE, or CAST operations on TIMESTAMP data type columns fails if loss of precision will result.")

