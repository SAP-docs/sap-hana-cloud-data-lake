<!-- loioa63eeb7884f210158f16b0a316e7e5e1 -->

# MAX\_JOIN\_ENUMERATION Option for Data Lake Relational Engine

Controls the maximum number of tables to be optimized for join order after optimizer simplifications have been applied.



<a name="loioa63eeb7884f210158f16b0a316e7e5e1__section_rv2_mvs_swb"/>

## Usage

This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa63eeb7884f210158f16b0a316e7e5e1__iq_refso_747"/>

## Default

15



<a name="loioa63eeb7884f210158f16b0a316e7e5e1__iq_refso_749"/>

## Remarks

Each FROM clause is limited to having at most 64 tables. In practice, however, the effective limit on the number of tables in a FROM clause is usually much lower, and is based partially on the complexity of the join relationships among those tables. That effective limit is constrained by the setting for MAX\_JOIN\_ENUMERATION. The optimizer will attempt to simplify the set of join relationships within a FROM clause. If those simplifications fail to reduce the set of the joins that must be simultaneously considered to no more than the current setting for MAX\_JOIN\_ENUMERATION, then the query will return an error.

The query optimizer simplifies its optimization of join order by separate handling of both lookup tables \(that is, nonselective dimension tables\) and tables that are effective Cartesian products. After simplification, it proceeds with optimizing the remaining tables for join order, up to the limit set by MAX\_JOIN\_ENUMERATION. If this limit is exceeded, the query is rejected with an error. The user can then either simplify the query or try increasing the limit.

