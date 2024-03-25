<!-- loiofd5cb635d5464947aed12b0669d4a1a0 -->

# Rebuilding Column Keys, Constraints,Comments, Grants, or Indexes on TIMESTAMP Data Type Columns in Data Lake Relational Engine

Once a column is converted, re-create any keys, constraints,comments, grants, or indexes associated with the original column.



<a name="loiofd5cb635d5464947aed12b0669d4a1a0__rebuild_columns_section1"/>

## Prerequisites

This data lake Relational Engine task can be completed when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.

The privileges required depend on the keys, constraint, comments, grants, or indexes begin created. See the specific statement for privileges details.



<a name="loiofd5cb635d5464947aed12b0669d4a1a0__rebuild_columns_section2"/>

## Context

Use the [ALTER TABLE Statement for Data Lake Relational Engine](../080-sql-statements/alter-table-statement-for-data-lake-relational-engine-39f1ec0.md) to add keys and constraints to columns.

Use the [COMMENT Statement for Data Lake Relational Engine](../080-sql-statements/comment-statement-for-data-lake-relational-engine-a615ad2.md) to add comments to columns.

Use the [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md) to grant object-level privileges to columns.

Use the [CREATE INDEX Statement for Data Lake Relational Engine](../080-sql-statements/create-index-statement-for-data-lake-relational-engine-a617ca4.md) to create indexes on columns.

