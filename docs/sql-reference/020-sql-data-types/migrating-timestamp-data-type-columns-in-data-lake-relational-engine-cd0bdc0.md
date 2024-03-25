<!-- loiocd0bdc0fda794bdeadbeaa033863f44f -->

# Migrating TIMESTAMP Data Type Columns in Data Lake Relational Engine

Migrate existing TIMESTAMP data type 6 digits of precision columns to 7-digits of precision.



The data type of a column cannot be changed. Instead, you create a new TIMESTAMP column using 7-digits of precision in the table, copy the data from the original column to the new column, drop the original column, and then \(optional\) rename the new column to that of the original column name. Once migrated, any SAP HANA database virtual table that points to a data lake Relational Engine table containing the migrated column continues to work.

