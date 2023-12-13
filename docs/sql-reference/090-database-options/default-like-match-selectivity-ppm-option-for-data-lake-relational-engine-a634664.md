<!-- loioa634664c84f2101583ecdbfe31ed14ef -->

# DEFAULT\_LIKE\_MATCH\_SELECTIVITY\_PPM Option for Data Lake Relational Engine

Provides default selectivity estimates \(in parts per million\) to the optimizer for most LIKE predicates.



<a name="loioa634664c84f2101583ecdbfe31ed14ef__section_rv2_mvs_swb"/>

## Usage

This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa634664c84f2101583ecdbfe31ed14ef__iq_refso_499"/>

## Default

150,000



<a name="loioa634664c84f2101583ecdbfe31ed14ef__iq_refso_501"/>

## Remarks

DEFAULT\_LIKE\_MATCH\_SELECTIVITY\_PPM sets the default selectivity for generic LIKE predicates, for example, LIKE '*<string%string\>*' where % is a wildcard character.

The optimizer relies on this option when other selectivity information is not available and the match string does not start with a set of constant characters followed by a single wildcard.

If the column has or a 1- or 2- or 3-byte FP index, the optimizer can get exact information and does not need to use this value.

You can also specify selectivity \(user-supplied condition hints\).

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[User-Supplied Condition Hints](../010-sql-language-elements/user-supplied-condition-hints-a5023f4.md "The selectivity of a condition is the fraction of the table’s rows that satisfy that condition.")

[DEFAULT\_LIKE\_RANGE\_SELECTIVITY\_PPM Option for Data Lake Relational Engine](default-like-range-selectivity-ppm-option-for-data-lake-relational-engine-a63494c.md "Provides default selectivity estimates (in parts per million) to the optimizer for leading constant LIKE predicates.")

[FP\_LOOKUP\_SIZE Optionfor Data Lake Relational Engine](fp-lookup-size-optionfor-data-lake-relational-engine-a63673f.md "Specifies the number of lookup pages and cache memory allocated for Lookup FP indexes in data lake Relational Engine databases.")

