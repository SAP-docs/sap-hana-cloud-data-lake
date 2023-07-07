<!-- loioa873d4b984f2101592ac80c2eed3effc -->

# FP\_NBIT\_ROLLOVER\_MAX\_MB Option for Data Lake Relational Engine

Sets a threshold for the total dictionary size for implicit NBit rollovers to Flat FP.



> ### Restriction:  
> This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa873d4b984f2101592ac80c2eed3effc__fp_nbit_rollover_default1"/>

## Default

16384 KB



<a name="loioa873d4b984f2101592ac80c2eed3effc__fp_nbit_rollover_dependencies1"/>

## Dependencies

FP\_NBIT\_ROLLOVER\_MAX\_MB applies to databases running where FP\_NBIT\_IQ15\_COMPATIBILITY is 'OFF.' If it is set to 'ON,' the database engine ignores this option.



<a name="loioa873d4b984f2101592ac80c2eed3effc__fp_nbit_rollover_remarks1"/>

## Remarks

FP\_NBIT\_AUTOSIZE\_LIMIT and FP\_NBIT\_LOOKUP\_MB establish a ceiling for sizing implicit NBit FPNBit rollovers:

-   If the total dictionary size per column does not exceed the FP\_NBIT\_ROLLOVER\_MAX\_MB, the columns. DML operations that exceed these values check the FP\_NBIT\_ROLLOVER\_MAX\_MB limit, which sets the dictionary size \(values and counts\) for implicit NBit column rolls over to a Flat FP.
-   If the dictionary size exceeds the FP\_NBIT\_ROLLOVER\_MAX\_MB limit and FP\_NBIT\_ENFORCE\_LIMITS='ON', DML operations throw an error and roll back.
-   columns. DML operations that exceed these valuesIf the dictionary size exceeds the FP\_NBIT\_ROLLOVER\_MAX\_MB limit and FP\_NBIT\_ENFORCE\_LIMITS='OFF' \(default\), DML operations keep running, and the NBit dictionary continues to grow.

`sp_iqindexmetadata` returns details about `Flat FP` or `NBit FP` columns. `sp_iqrebuildindex` can change explicit or implicit `NBit FP` column limits, or reformat the default column index as `Flat FP` or `NBit FP`.



<a name="loioa873d4b984f2101592ac80c2eed3effc__fp_nbit_rollover_additional1"/>

## Additional Information

*sp\_iqrebuildindex Procedure* and *sp\_iqindexmetadata Procedure* in *SAP HANA Cloud, Data Lake SQL Reference for Data Lake Relational Engine*.

**Related Information**  


[FP\_NBIT\_AUTOSIZE\_LIMIT Option for Data Lake Relational Engine](fp-nbit-autosize-limit-option-for-data-lake-relational-engine-a873755.md "Limits the number of distinct values in columns that implicitly load as NBit FP.")

[FP\_NBIT\_ENFORCE\_LIMITS Option for Data Lake Relational Engine](fp-nbit-enforce-limits-option-for-data-lake-relational-engine-a874045.md "Enforces sizing limits for explicit and implicit NBit columns.")

[FP\_NBIT\_IQ15\_COMPATIBILITY Option for Data Lake Relational Engine](fp-nbit-iq15-compatibility-option-for-data-lake-relational-engine-a874375.md "Provides support for tokenized FP indexes similar to that available in data lake Relational Engine.")

[FP\_NBIT\_LOOKUP\_MB Option for Data Lake Relational Engine](fp-nbit-lookup-mb-option-for-data-lake-relational-engine-a873a52.md "Limits the total dictionary size per column for implicit NBit FP columns.")

[FP\_NBIT\_ROLLOVER\_MAX\_MB Option for Data Lake Relational Engine](fp-nbit-rollover-max-mb-option-for-data-lake-relational-engine-a873d4b.md "Sets a threshold for the total dictionary size for implicit NBit rollovers to Flat FP.")

[sp\_iqrebuildindex Procedure for Data Lake Relational Engine](../060-stored-procedures/sp-iqrebuildindex-procedure-for-data-lake-relational-engine-a5b342e.md "Rebuilds column indexes.")

[sp\_iqindexmetadata Procedure for Data Lake Relational Engine](../060-stored-procedures/sp-iqindexmetadata-procedure-for-data-lake-relational-engine-a5ad0e4.md "Displays index metadata for a given index.")

[FP_NBIT_ROLLOVER_MAX_MB Option for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/9035f14a9b62495a9278924113575b2c.html "Sets a threshold for the total dictionary size for implicit NBit rollovers to Flat FP.") :arrow_upper_right:

