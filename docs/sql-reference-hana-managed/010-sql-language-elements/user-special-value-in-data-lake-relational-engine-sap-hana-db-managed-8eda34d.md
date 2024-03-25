<!-- loio8eda34d1c8cc4b0783bf99b11d4e1291 -->

# USER Special Value in Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns a string that contains the user ID of the current connection.



<a name="loio8eda34d1c8cc4b0783bf99b11d4e1291__section_agt_pxr_btb"/>

## Usage

Data lake Relational Engine \(SAP HANA DB-Managed\) special values can be used when connected as follows:

-   To use a special value as a column default when creating a table, you must be:
    -   Connected to SAP HANA database as a SAP HANA database user.

-   To return an expression as part of a SELECT statement that returns a value, you must be:
    -   Connected to SAP HANA database as a SAP HANA database user.




<a name="loio8eda34d1c8cc4b0783bf99b11d4e1291__section_elz_cgr_btb"/>

## Data Type

STRING



<a name="loio8eda34d1c8cc4b0783bf99b11d4e1291__section_i2z_dgr_btb"/>

## Remarks

USER can be used as a default value in columns with character data types.

On UPDATE, columns with a default value of USER aren’t changed.



<a name="loio8eda34d1c8cc4b0783bf99b11d4e1291__section_gn4_2gr_btb"/>

## Standards


<dl>
<dt><b>

ANSI/ISO SQL Standard

</b></dt>
<dd>

Not in the standard.



</dd>
</dl>

**Related Information**  


[CURRENT TIMESTAMP Special Value in Data Lake Relational Engine \(SAP HANA DB-Managed\)](current-timestamp-special-value-in-data-lake-relational-engine-sap-hana-db-managed-4bbfdd6.md "Combines CURRENT DATE and CURRENT TIME to form a TIMESTAMP value containing the year, month, day, hour, minute, second, and fraction of a second.")

[CURRENT USER Special Value in Data Lake Relational Engine \(SAP HANA DB-Managed\)](current-user-special-value-in-data-lake-relational-engine-sap-hana-db-managed-336e6f1.md "Returns a string that contains the user ID of the current connection.")

