<!-- loio520ce6c6c90f47769eb2f1ddafa8bf49 -->

# TIMESTAMP Data Type Precision in Data Lake Relational Engine

Precision conflicts between TIMESTAMP data types result in data loss.





### 

The TIMESTAMP data type in SAP HANA database uses 7-digits of precision. The TIMESTAMP data type in data lake Relational Engine uses 6 or 7-digits of precision. If you import 7-digits of data into 6-digits of precision columns, then the last digit of the data source is truncated resulting in data loss. To avoid losing data, the data lake Relational Engine columns need to be created as 7-digits of precision columns prior to importing the 7-digits of precision data.

Precision for TIMESTAMP data type columns is controlled by the TIMESTAMP\_COLUMNS\_AS\_DATETIMEX database option. This option controls whether TIMESTAMP data type columns in data lake Relational Engine support 6 or 7-digits of precision.

When set to ON, **new** TIMESTAMP data type columns use 7-digits of precision. When set to OFF, **new** TIMESTAMP data type columns use 6-digits of precision. Once set, this option has **no impact** on the precision of **existing** TIMESTAMP columns; they **retain** their original precision. Only new TIMESTAMP columns created after the database option is enabled use the new default of 7-digits.

The default for the TIMESTAMP\_COLUMNS\_AS\_DATETIMEX database option depends on when your instance was created. See [TIMESTAMP\_COLUMNS\_AS\_DATETIMEX Option for Data Lake Relational Engine](../090-database-options/timestamp-columns-as-datetimex-option-for-data-lake-relational-engine-082fdf9.md).

> ### Caution:  
> Once data is truncated, the truncated data cannot be recovered. Enabling the TIMESTAMP\_COLUMNS\_AS\_DATETIMEX database option does **not** recover the truncated data. Migrating the columns will not recover the truncated data, but **will** prevent future truncations during future data loads.

**Related Information**  


[CAST Function \[Data Type Conversion\] for Data Lake Relational Engine](../050-system-sql-functions/cast-function-data-type-conversion-for-data-lake-relational-engine-a53996d.md "Returns the value of an expression converted to a supplied data type.")

[TIMESTAMP\_RTRUNCATION Option for Data Lake Relational Engine](../090-database-options/timestamp-rtruncation-option-for-data-lake-relational-engine-dbb08c7.md "Controls whether INSERT, UPDATE, or CAST operations on TIMESTAMP data type columns fails if loss of precision will result.")

[UPDATE Statement for Data Lake Relational Engine](../080-sql-statements/update-statement-for-data-lake-relational-engine-a628441.md "Modifies existing rows of a single table, or a view that contains only one table.")

[INSERT Statement for Data Lake Relational Engine](../080-sql-statements/insert-statement-for-data-lake-relational-engine-a61fdef.md "Inserts a single row or a selection of rows, from elsewhere in the current database, into the table. This command can also insert a selection of rows from another database into the table.")

[TIMESTAMP\_COLUMNS\_AS\_DATETIMEX Option for Data Lake Relational Engine](../090-database-options/timestamp-columns-as-datetimex-option-for-data-lake-relational-engine-082fdf9.md "Controls whether DATETIMEX data type columns are automatically created when TIMESTAMPS data type columns are requested.")

[TIMESTAMP Data Type Precision in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/5cbca14157bc452c88126325667e4342.html "Precision conflicts between TIMESTAMP data types result in data loss.") :arrow_upper_right:

