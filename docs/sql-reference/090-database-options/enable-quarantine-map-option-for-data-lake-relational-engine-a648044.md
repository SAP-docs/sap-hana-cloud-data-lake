<!-- loioa6480443120d49478a5faeb81417fd49 -->

# ENABLE\_QUARANTINE\_MAP Option for Data Lake Relational Engine

Controls whether data lake Relational Engine quarantines corrupted disk blocks to prevent those blocks from being reallocated until they are repaired.



<a name="loioa6480443120d49478a5faeb81417fd49__section_rv2_mvs_swb"/>

## Usage

This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa6480443120d49478a5faeb81417fd49__section_eky_bzj_jfb"/>

## Default

OFF



<a name="loioa6480443120d49478a5faeb81417fd49__section_zsp_kzj_jfb"/>

## Remarks

This option lets data lake Relational Engine quarantine corrupted disk blocks when detected, for example, when reading an invalid disk header.

Quarantined blocks are unavailable for allocation and if owned by a data structure, will not be deallocated. The DBCC utility detects when unowned allocated blocks are quarantined and reports them, but does not count them as errors.

**Related Information**  


[sp\_iqcheckdb System Procedure for Data Lake Relational Engine](../060-stored-procedures/sp-iqcheckdb-system-procedure-for-data-lake-relational-engine-a59d2e0.md "Checks validity of the current database. Optionally corrects allocation problems for dbspaces or databases. sp_iqcheckdb does not check a partitioned table if partitioned data exists on offline dbspaces.")

[sp\_iqquarantinedblocks System Procedure for Data Lake Relational Engine](../060-stored-procedures/sp-iqquarantinedblocks-system-procedure-for-data-lake-relational-engine-649c0a5.md "Displays information about block numbers that cannot be reused because they hold corrupt objects, and will remain in use until the corruption is repaired..")

[sp\_iqquarantinedblocksclear System Procedure for Data Lake Relational Engine](../060-stored-procedures/sp-iqquarantinedblocksclear-system-procedure-for-data-lake-relational-engine-5a89726.md "Clears the system quarantine map, removing all physical block numbers for any quarantined data.")

