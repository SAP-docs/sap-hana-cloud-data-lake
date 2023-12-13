<!-- loio3a6a1e34bc754fe2bdb9412884c6a57f -->

# FP\_NBIT\_LOOKUP\_MB Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Limits the total dictionary size per column for implicit NBit FP columns.



<a name="loio3a6a1e34bc754fe2bdb9412884c6a57f__section_jc5_4pn_vwb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) database option is set by the system and cannot be changed.



<a name="loio3a6a1e34bc754fe2bdb9412884c6a57f__section_kjs_x3s_lrb"/>

## Default

64 \(MB\)



<a name="loio3a6a1e34bc754fe2bdb9412884c6a57f__section_jlh_chp_ywb"/>

## Remarks

FP\_NBIT\_AUTOSIZE\_LIMIT and FP\_NBIT\_LOOKUP\_MB establish a ceiling for sizing implicit NBit columns. As long as the number of distinct values is less than FP\_NBIT\_AUTOSIZE\_LIMIT and the total dictionary size \(values and counts\) per column is less the FP\_NBIT\_LOOKUP\_MB, the column loads with an NBit FP index. Limits are enforced by the FP\_NBIT\_ENFORCE\_LIMITS option.

DML operations that exceed the FP\_NBIT\_LOOKUP\_MB limit rollover to a Flat FP index.

If an operation exceeds FP\_NBIT\_LOOKUP\_MB and FP\_NBIT\_ROLLOVER\_MAX\_MB limits, and FP\_NBIT\_ENFORCE\_LIMITS is set to OFF, the NBit FP transitions to the next NBit level.

**Related Information**  


[FP\_NBIT\_AUTOSIZE\_LIMIT Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)](fp-nbit-autosize-limit-option-for-data-lake-relational-engine-sap-hana-db-managed-829744c.md "Limits the number of distinct values in columns that implicitly load as NBit FP.")

[FP\_NBIT\_ENFORCE\_LIMITS Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)](fp-nbit-enforce-limits-option-for-data-lake-relational-engine-sap-hana-db-managed-2e6a10d.md "Enforces sizing limits for explicit and implicit NBit columns.")

[FP\_NBIT\_ROLLOVER\_MAX\_MB Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)](fp-nbit-rollover-max-mb-option-for-data-lake-relational-engine-sap-hana-db-managed-9035f14.md "Sets a threshold for the total dictionary size for implicit NBit rollovers to Flat FP.")

[FP_NBIT_LOOKUP_MB Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/a873a52f84f2101588a9c5a2df1d1389.html "Limits the total dictionary size per column for implicit NBit FP columns.") :arrow_upper_right:

