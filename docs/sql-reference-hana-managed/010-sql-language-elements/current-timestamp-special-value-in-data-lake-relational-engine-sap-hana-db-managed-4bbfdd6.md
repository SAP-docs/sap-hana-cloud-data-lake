<!-- loio4bbfdd6d4312481d99df98a23b4cc3dc -->

# CURRENT TIMESTAMP Special Value in Data Lake Relational Engine \(SAP HANA DB-Managed\)

Combines CURRENT DATE and CURRENT TIME to form a TIMESTAMP value containing the year, month, day, hour, minute, second, and fraction of a second.



<a name="loio4bbfdd6d4312481d99df98a23b4cc3dc__section_agt_pxr_btb"/>

## Usage

Data lake Relational Engine \(SAP HANA DB-Managed\) special values can be used when connected as follows:

-   To use a special value as a column default when creating a table, you must be:
    -   Connected to SAP HANA database as a SAP HANA database user.

-   To return an expression as part of a SELECT statement that returns a value, you must be:
    -   Connected to SAP HANA database as a SAP HANA database user.




<a name="loio4bbfdd6d4312481d99df98a23b4cc3dc__section_dtd_xbr_btb"/>

## Data Type

TIMESTAMP



<a name="loio4bbfdd6d4312481d99df98a23b4cc3dc__section_a42_ybr_btb"/>

## Remarks

As with CURRENT TIME, the accuracy of the fraction of a second is limited by the system clock.

CURRENT TIMESTAMP defaults to three digits.



<a name="loio4bbfdd6d4312481d99df98a23b4cc3dc__section_ggr_ybr_btb"/>

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


[CURRENT USER Special Value in Data Lake Relational Engine \(SAP HANA DB-Managed\)](current-user-special-value-in-data-lake-relational-engine-sap-hana-db-managed-336e6f1.md "Returns a string that contains the user ID of the current connection.")

[USER Special Value in Data Lake Relational Engine \(SAP HANA DB-Managed\)](user-special-value-in-data-lake-relational-engine-sap-hana-db-managed-8eda34d.md "Returns a string that contains the user ID of the current connection.")

