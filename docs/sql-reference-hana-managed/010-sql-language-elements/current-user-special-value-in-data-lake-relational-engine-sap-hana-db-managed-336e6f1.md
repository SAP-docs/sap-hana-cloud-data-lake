<!-- loio336e6f16ef0b4dbeac5a0f16a1e8b15f -->

# CURRENT USER Special Value in Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns a string that contains the user ID of the current connection.



<a name="loio336e6f16ef0b4dbeac5a0f16a1e8b15f__section_agt_pxr_btb"/>

## Usage

Data lake Relational Engine \(SAP HANA DB-Managed\) special values can be used when connected as follows:

-   To use a special value as a column default when creating a table, you must be:
    -   Connected to SAP HANA database as a SAP HANA database user.

-   To return an expression as part of a SELECT statement that returns a value, you must be:
    -   Connected to SAP HANA database as a SAP HANA database user.




<a name="loio336e6f16ef0b4dbeac5a0f16a1e8b15f__section_xlx_ndr_btb"/>

## Data Type

STRING

CURRENT USER can be used as a default value in columns with character data types.



<a name="loio336e6f16ef0b4dbeac5a0f16a1e8b15f__section_kfx_4dr_btb"/>

## Remarks

CURRENT USER can be used as a default value in columns with character data types.

On UPDATE, columns with a default value of CURRENT USER are not changed.



<a name="loio336e6f16ef0b4dbeac5a0f16a1e8b15f__section_ulg_pdr_btb"/>

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

[USER Special Value in Data Lake Relational Engine \(SAP HANA DB-Managed\)](user-special-value-in-data-lake-relational-engine-sap-hana-db-managed-8eda34d.md "Returns a string that contains the user ID of the current connection.")

