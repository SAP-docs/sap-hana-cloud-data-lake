<!-- loioa63be24b84f210158835e52f5dcf32ee -->

# JOIN\_SIMPLIFICATION\_THRESHOLD Option for Data Lake Relational Engine

Controls the minimum number of tables being joined together before any join optimizer simplifications are applied.



<a name="loioa63be24b84f210158835e52f5dcf32ee__section_rv2_mvs_swb"/>

## Usage

This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa63be24b84f210158835e52f5dcf32ee__iq_refso_673"/>

## Default

12



<a name="loioa63be24b84f210158835e52f5dcf32ee__iq_refso_675"/>

## Remarks

The query optimizer simplifies its optimization of join order by separate handling of both lookup tables \(that is, nonselective dimension tables\) and tables that are effective Cartesian products. After simplification, it optimizes the remaining tables for join order, up to the limit set by MAX\_JOIN\_ENUMERATION.

**Related Information**  


[MAX\_JOIN\_ENUMERATION Option for Data Lake Relational Engine](max-join-enumeration-option-for-data-lake-relational-engine-a63eeb7.md "Controls the maximum number of tables to be optimized for join order after optimizer simplifications have been applied.")

