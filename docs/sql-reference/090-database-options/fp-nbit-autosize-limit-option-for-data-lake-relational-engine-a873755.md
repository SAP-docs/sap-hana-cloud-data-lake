<!-- loioa873755184f21015a76ff1329f851c5d -->

# FP\_NBIT\_AUTOSIZE\_LIMIT Option for Data Lake Relational Engine

Limits the number of distinct values in columns that implicitly load as NBit FP.



<a name="loioa873755184f21015a76ff1329f851c5d__section_rv2_mvs_swb"/>

## Usage

This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa873755184f21015a76ff1329f851c5d__fp_nbit_autosize_limit_default1"/>

## Default

1,048,576



<a name="loioa873755184f21015a76ff1329f851c5d__fp_nbit_autosize_limit_depend1"/>

## Dependencies

FP\_NBIT\_AUTOSIZE\_LIMIT applies to databases running where FP\_NBIT\_IQ15\_COMPATIBILITY is set to OFF. If ON, the database engine ignores this option.



<a name="loioa873755184f21015a76ff1329f851c5d__fp_nbit_autosize_limit_remarks1"/>

## Remarks

FP\_NBIT\_AUTOSIZE\_LIMIT limits the number of distinct values in all newly created columns without an explicit IQ UNIQUE setting.

FP\_NBIT\_AUTOSIZE\_LIMIT and FP\_NBIT\_LOOKUP\_MB establish a ceiling for sizing NBit columns during data loads. As long as the number of distinct values is less than FP\_NBIT\_AUTOSIZE\_LIMIT and the total dictionary size \(values and counts\) per column is less the FP\_NBIT\_LOOKUP\_MB, the column loads as an NBit. If the load exceeds the FP\_NBIT\_AUTOSIZE\_LIMIT but is less than FP\_NBIT\_ROLLOVER\_MAX\_MB, the column rolls over to Flat FP.

If FP\_ENFORCE\_LIMITS is set to ON and DML operations exceed the FP\_NBIT\_ROLLOVER\_MAX\_MB, the operations roll back and report an error. If the FP\_NBIT\_ENFORCE\_LIMITS is set to OFF, the column transitions to the next NBit level.

`sp_iqindexmetadata` returns details about `Flat FP` or `NBit FP` columns. `sp_iqrebuildindex` can change explicit or implicit `NBit FP` column limits, or reformat the default column index as `Flat FP` or `NBit FP`.



<a name="loioa873755184f21015a76ff1329f851c5d__fp_nbit_autosize_limit_additional1"/>

## Additional Information

-   *SAP HANA Cloud, Data Lake SQL Reference for Data Lake Relational Engine \> System Procedures \> Alphabetical List of System Stored Procedures \> sp\_iqrebuildindex*
-   *SAP HANA Cloud, Data Lake SQL Reference for Data Lake Relational Engine \> System Procedures » Alphabetical List of System Stored Procedures \> sp\_iqindexmetadata*

**Related Information**  


[FP_NBIT_AUTOSIZE_LIMIT Option for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/829744c675a441899d9aa46a28873eab.html "Limits the number of distinct values in columns that implicitly load as NBit FP.") :arrow_upper_right:

[FP\_NBIT\_ENFORCE\_LIMITS Option for Data Lake Relational Engine](fp-nbit-enforce-limits-option-for-data-lake-relational-engine-a874045.md "Enforces sizing limits for explicit and implicit NBit columns.")

[FP\_NBIT\_IQ15\_COMPATIBILITY Option for Data Lake Relational Engine](fp-nbit-iq15-compatibility-option-for-data-lake-relational-engine-a874375.md "Provides support for tokenized FP indexes similar to that available in data lake Relational Engine.")

[FP\_NBIT\_LOOKUP\_MB Option for Data Lake Relational Engine](fp-nbit-lookup-mb-option-for-data-lake-relational-engine-a873a52.md "Limits the total dictionary size per column for implicit NBit FP columns.")

[FP\_NBIT\_ROLLOVER\_MAX\_MB Option for Data Lake Relational Engine](fp-nbit-rollover-max-mb-option-for-data-lake-relational-engine-a873d4b.md "Sets a threshold for the total dictionary size for implicit NBit rollovers to Flat FP.")

