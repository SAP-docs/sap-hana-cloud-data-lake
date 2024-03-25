<!-- loioa873a52f84f2101588a9c5a2df1d1389 -->

# FP\_NBIT\_LOOKUP\_MB Option for Data Lake Relational Engine

Limits the total dictionary size per column for implicit NBit FP columns.



<a name="loioa873a52f84f2101588a9c5a2df1d1389__section_rv2_mvs_swb"/>

## Usage

This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa873a52f84f2101588a9c5a2df1d1389__fp_nbit_lookup_mb_default1"/>

## Default

64 \(MB\)



<a name="loioa873a52f84f2101588a9c5a2df1d1389__fp_nbit_lookup_mb_depend1"/>

## Dependencies

FP\_NBIT\_LOOKUP\_MB applies to databases running where FP\_NBIT\_IQ15\_COMPATIBILITY is set to OFF. If ON, the database engine ignores this option.



<a name="loioa873a52f84f2101588a9c5a2df1d1389__fp_nbit_lookup_mb_remarks1"/>

## Remarks

FP\_NBIT\_AUTOSIZE\_LIMIT and FP\_NBIT\_LOOKUP\_MB establish a ceiling for sizing implicit NBit columns. As long as the number of distinct values is less than FP\_NBIT\_AUTOSIZE\_LIMIT and the total dictionary size \(values and counts\) per column is less the FP\_NBIT\_LOOKUP\_MB, the column loads with an NBit FP index. Limits are enforced by the FP\_NBIT\_ENFORCE\_LIMITS option.

DML operations that exceed the FP\_NBIT\_LOOKUP\_MB limit rollover to a Flat FP index.

If an operation exceeds FP\_NBIT\_LOOKUP\_MB and FP\_NBIT\_ROLLOVER\_MAX\_MB limits, and FP\_NBIT\_ENFORCE\_LIMITS is set to OFF, the NBit FP transitions to the next NBit level.

`sp_iqindexmetadata` returns details about `Flat FP` or `NBit FP` columns. `sp_iqrebuildindex` can change explicit or implicit `NBit FP` column limits, or reformat the default column index as `Flat FP` or `NBit FP`.



<a name="loioa873a52f84f2101588a9c5a2df1d1389__fp_nbit_lookup_mb_additional1"/>

## Additional Information

*sp\_iqrebuildindex Procedure* and *sp\_iqindexmetadata Procedure* in *SAP HANA Cloud, Data Lake SQL Reference for Data Lake Relational Engine*.

**Related Information**  


[FP\_NBIT\_AUTOSIZE\_LIMIT Option for Data Lake Relational Engine](fp-nbit-autosize-limit-option-for-data-lake-relational-engine-a873755.md "Limits the number of distinct values in columns that implicitly load as NBit FP.")

[FP\_NBIT\_ENFORCE\_LIMITS Option for Data Lake Relational Engine](fp-nbit-enforce-limits-option-for-data-lake-relational-engine-a874045.md "Enforces sizing limits for explicit and implicit NBit columns.")

[FP\_NBIT\_IQ15\_COMPATIBILITY Option for Data Lake Relational Engine](fp-nbit-iq15-compatibility-option-for-data-lake-relational-engine-a874375.md "Provides support for tokenized FP indexes similar to that available in data lake Relational Engine.")

[FP\_NBIT\_ROLLOVER\_MAX\_MB Option for Data Lake Relational Engine](fp-nbit-rollover-max-mb-option-for-data-lake-relational-engine-a873d4b.md "Sets a threshold for the total dictionary size for implicit NBit rollovers to Flat FP.")

[sp\_iqindexmetadata Procedure for Data Lake Relational Engine](../060-stored-procedures/sp-iqindexmetadata-procedure-for-data-lake-relational-engine-a5ad0e4.md "Displays index metadata for a given index.")

[sp\_iqrebuildindex Procedure for Data Lake Relational Engine](../060-stored-procedures/sp-iqrebuildindex-procedure-for-data-lake-relational-engine-a5b342e.md "Rebuilds column indexes.")

[FP_NBIT_LOOKUP_MB Option for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/3a6a1e34bc754fe2bdb9412884c6a57f.html "Limits the total dictionary size per column for implicit NBit FP columns.") :arrow_upper_right:

