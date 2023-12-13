<!-- loio74de36ec9d494ef5a2b4b0bf95536805 -->

# LAST USER Special Value in Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the name of the user who last modified the row.



<a name="loio74de36ec9d494ef5a2b4b0bf95536805__section_agt_pxr_btb"/>

## Usage

Data lake Relational Engine \(SAP HANA DB-Managed\) special values can be used when connected as follows:

-   To use a special value as a column default when creating a table, you must be:
    -   Connected to SAP HANA database as a SAP HANA database user and using the SAP HANA database REMOTE\_EXECUTE procedure

-   To return an expression as part of a SELECT statement that returns a value, you must be:
    -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXEUCTE\_QUERY function.




<a name="loio74de36ec9d494ef5a2b4b0bf95536805__section_vrg_3qr_btb"/>

## Data Type

STRING



<a name="loio74de36ec9d494ef5a2b4b0bf95536805__section_tsp_3qr_btb"/>

## Remarks

On INSERT and LOAD, this constant has the same effect as CURRENT USER. On UPDATE, if a column with a default value of LAST USER is not explicitly modified, it is changed to the name of the current user.

When combined with the DEFAULT TIMESTAMP, a default value of LAST USER can be used to record \(in separate columns\) both the user and the date and time a row was last changed.

LAST USER can be used as a default value in columns with character data types.

**Related Information**  


[CURRENT TIMESTAMP Special Value in Data Lake Relational Engine \(SAP HANA DB-Managed\)](current-timestamp-special-value-in-data-lake-relational-engine-sap-hana-db-managed-4bbfdd6.md "Combines CURRENT DATE and CURRENT TIME to form a TIMESTAMP value containing the year, month, day, hour, minute, second, and fraction of a second.")

[CURRENT USER Special Value in Data Lake Relational Engine \(SAP HANA DB-Managed\)](current-user-special-value-in-data-lake-relational-engine-sap-hana-db-managed-336e6f1.md "Returns a string that contains the user ID of the current connection.")

[USER Special Value in Data Lake Relational Engine \(SAP HANA DB-Managed\)](user-special-value-in-data-lake-relational-engine-sap-hana-db-managed-8eda34d.md "Returns a string that contains the user ID of the current connection.")

