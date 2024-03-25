<!-- loio098e867319864e67a7665c8338568cad -->

# CURRENT TIME Special Value in Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the current hour, minute, second, and fraction of a second.



<a name="loio098e867319864e67a7665c8338568cad__section_agt_pxr_btb"/>

## Usage

Data lake Relational Engine \(SAP HANA DB-Managed\) special values can be used when connected as follows:

-   To use a special value as a column default when creating a table, you must be:
    -   Connected to SAP HANA database as a SAP HANA database user.

-   To return an expression as part of a SELECT statement that returns a value, you must be:
    -   Connected to SAP HANA database as a SAP HANA database user.




<a name="loio098e867319864e67a7665c8338568cad__section_al4_kbr_btb"/>

## Data Type

TIME



<a name="loio098e867319864e67a7665c8338568cad__section_wzw_kbr_btb"/>

## Remarks

The fraction of a second is stored to six decimal places, but the accuracy of the current time is limited by the accuracy of the system clock.



<a name="loio098e867319864e67a7665c8338568cad__section_dnk_mbr_btb"/>

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

