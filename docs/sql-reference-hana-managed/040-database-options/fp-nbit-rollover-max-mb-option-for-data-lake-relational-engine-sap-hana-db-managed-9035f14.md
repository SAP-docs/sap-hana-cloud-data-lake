<!-- loio9035f14a9b62495a9278924113575b2c -->

# FP\_NBIT\_ROLLOVER\_MAX\_MB Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Sets a threshold for the total dictionary size for implicit NBit rollovers to Flat FP.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) database option is set by the system and cannot be changed.



<a name="loio9035f14a9b62495a9278924113575b2c__section_o4k_bks_lrb"/>

## Default

16384 KB



<a name="loio9035f14a9b62495a9278924113575b2c__section_zht_2jp_ywb"/>

## Remarks

FP\_NBIT\_AUTOSIZE\_LIMIT and FP\_NBIT\_LOOKUP\_MB establish a ceiling for sizing implicit NBit FPNBit rollovers:

-   If the total dictionary size per column does not exceed the FP\_NBIT\_ROLLOVER\_MAX\_MB, the columns. DML operations that exceed these values check the FP\_NBIT\_ROLLOVER\_MAX\_MB limit, which sets the dictionary size \(values and counts\) for implicit NBit column rolls over to a Flat FP.
-   If the dictionary size exceeds the FP\_NBIT\_ROLLOVER\_MAX\_MB limit and FP\_NBIT\_ENFORCE\_LIMITS='ON', DML operations throw an error and roll back.
-   columns. DML operations that exceed these valuesIf the dictionary size exceeds the FP\_NBIT\_ROLLOVER\_MAX\_MB limit and FP\_NBIT\_ENFORCE\_LIMITS='OFF' \(default\), DML operations keep running, and the NBit dictionary continues to grow.

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[FP\_NBIT\_AUTOSIZE\_LIMIT Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)](fp-nbit-autosize-limit-option-for-data-lake-relational-engine-sap-hana-db-managed-829744c.md "Limits the number of distinct values in columns that implicitly load as NBit FP.")

[FP\_NBIT\_ENFORCE\_LIMITS Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)](fp-nbit-enforce-limits-option-for-data-lake-relational-engine-sap-hana-db-managed-2e6a10d.md "Enforces sizing limits for explicit and implicit NBit columns.")

[FP\_NBIT\_LOOKUP\_MB Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)](fp-nbit-lookup-mb-option-for-data-lake-relational-engine-sap-hana-db-managed-3a6a1e3.md "Limits the total dictionary size per column for implicit NBit FP columns.")

[FP_NBIT_ROLLOVER_MAX_MB Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a873d4b984f2101592ac80c2eed3effc.html "Sets a threshold for the total dictionary size for implicit NBit rollovers to Flat FP.") :arrow_upper_right:

