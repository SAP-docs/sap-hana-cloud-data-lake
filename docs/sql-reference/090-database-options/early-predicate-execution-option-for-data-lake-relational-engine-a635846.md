<!-- loioa635846284f21015a53bd0bf89909d0d -->

# EARLY\_PREDICATE\_EXECUTION Option for Data Lake Relational Engine

Controls whether simple local predicates are executed before query optimization.



<a name="loioa635846284f21015a53bd0bf89909d0d__section_rv2_mvs_swb"/>

## Usage

This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa635846284f21015a53bd0bf89909d0d__iq_refso_520"/>

## Default

ON



<a name="loioa635846284f21015a53bd0bf89909d0d__iq_refso_522"/>

## Remarks

This option allows the optimizer finds, prepares, and executes predicates containing only local columns and constraints before query optimization, including join ordering, join algorithm selection, and grouping algorithm selection, so that the values of “Estimated Result Rows” in the query plan are more precise.

Data lake Relational Engine executes the local predicates for all queries before generating a query plan, even when the NOEXEC option is ON. The generated query plan is the same as the runtime plan.

This information is included in the query plan for the root node:

-   Threads used for executing local invariant predicates – if greater than 1, indicates parallel execution of local invariant predicates.
-   Early\_Predicate\_Execution – indicates if the option is OFF.
-   Time of Cursor Creation – the time of cursor creation.

The simple predicates for which execution is controlled by this option are referred to as invariant predicates in the query plan. This information is included in the query plan for a leaf node, if there are any local invariant predicates on the node:

-   Generated Post Invariant Predicate Rows – actual result after executing local invariant predicate
-   Estimated Post Invariant Predicate Rows – calculated by using estimated local invariant predicates selectivity
-   Time of Condition Start – starting time of the execution of local invariant predicates
-   Time of Condition Done – ending time of the execution of local invariant predicates
-   Elapsed Condition Time – elapsed time for executing local invariant predicates

