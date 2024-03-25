<!-- loio80aec2f8ded74780a42f98108995df47 -->

# DatalakeHDBCompatibility Alert in Data Lake Relational Engine

A warning of possible precision conflicts between data lake Relational Engine and SAP HANA database TIMESTAMP data types. These conflicts could result in data loss.



The DatalakeHDBCompatibility alert is generated when SAP HANA Cloud detects a data lake Relational Engine instance configured to be maximally compatible with SAP HANA database that also has data lake Relational Engine tables containing TIMESTAMP data type columns of 6-digits of precision.

The TIMESTAMP data type in SAP HANA database uses 7-digits of precision while the data lake Relational Engine TIMESTAMP data type can use 6 or 7-digits of precision. If you load 7-digits of precision data into 6-digits of precision columns, then the last digit of the source data is truncated resulting in data loss. To avoid losing data, ensure that the data lake Relational Engine TIMESTAMP columns are configured to use 7-digits of precision prior to importing 7-digit data.

> ### Note:  
> SAP HANA Cloud can detect the existence of data lake Relational Engine instances configured for maximum compatibility with SAP HANA database that also contain data lake Relational Engine tables with TIMESTAMP data type columns of 6-digits of precision. However, it cannot determine if a remote source between the SAP HANA database and data lake Relational Engine instances exists. Alerts for data lake Relational Engine instances with no connection to SAP HANA database instances, can be ignored.
> 
> Alerts for data lake Relational Engine instances not connected to SAP HANA database instances cannot be disabled. They will continue to appear until the TIMESTAMP columns are migrated to 7-digits. See [Migrating TIMESTAMP Data Type Columns in Data Lake Relational Engine](migrating-timestamp-data-type-columns-in-data-lake-relational-engine-cd0bdc0.md).

