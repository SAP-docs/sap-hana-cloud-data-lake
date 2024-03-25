<!-- loio829744c675a441899d9aa46a28873eab -->

# FP\_NBIT\_AUTOSIZE\_LIMIT Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Limits the number of distinct values in columns that implicitly load as NBit FP.



<a name="loio829744c675a441899d9aa46a28873eab__section_jc5_4pn_vwb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) database option is set by the system and cannot be changed.



<a name="loio829744c675a441899d9aa46a28873eab__section_qfz_vb3_3rb"/>

## Default

1,048,576



<a name="loio829744c675a441899d9aa46a28873eab__section_erq_zkp_ywb"/>

## Remarks

FP\_NBIT\_AUTOSIZE\_LIMIT limits the number of distinct values in all newly created columns without an explicit IQ UNIQUE setting.

FP\_NBIT\_AUTOSIZE\_LIMIT and FP\_NBIT\_LOOKUP\_MB establish a ceiling for sizing NBit columns during data loads. As long as the number of distinct values is less than FP\_NBIT\_AUTOSIZE\_LIMIT and the total dictionary size \(values and counts\) per column is less the FP\_NBIT\_LOOKUP\_MB, the column loads as an NBit. If the load exceeds the FP\_NBIT\_AUTOSIZE\_LIMIT but is less than FP\_NBIT\_ROLLOVER\_MAX\_MB, the column rolls over to Flat FP.

If FP\_ENFORCE\_LIMITS is set to ON and DML operations exceed the FP\_NBIT\_ROLLOVER\_MAX\_MB, the operations roll back and report an error. If the FP\_NBIT\_ENFORCE\_LIMITS is set to OFF, the column transitions to the next NBit level.

**Related Information**  


[FP\_NBIT\_LOOKUP\_MB Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)](fp-nbit-lookup-mb-option-for-data-lake-relational-engine-sap-hana-db-managed-3a6a1e3.md "Limits the total dictionary size per column for implicit NBit FP columns.")

[FP\_NBIT\_ROLLOVER\_MAX\_MB Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)](fp-nbit-rollover-max-mb-option-for-data-lake-relational-engine-sap-hana-db-managed-9035f14.md "Sets a threshold for the total dictionary size for implicit NBit rollovers to Flat FP.")

[FP\_NBIT\_ENFORCE\_LIMITS Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)](fp-nbit-enforce-limits-option-for-data-lake-relational-engine-sap-hana-db-managed-2e6a10d.md "Enforces sizing limits for explicit and implicit NBit columns.")

[FP_NBIT_AUTOSIZE_LIMIT Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/a873755184f21015a76ff1329f851c5d.html "Limits the number of distinct values in columns that implicitly load as NBit FP.") :arrow_upper_right:

