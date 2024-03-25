<!-- loiod868b12b173440f49bf3e9dcd8d32d3f -->

# Rebuilding Column Keys, Constraints, or Indexes on TIMESTAMP Data Type Columns in Data Lake Relational Engine \(SAP HANA DB-Managed\)

Once a column is converted, re-create any keys, constraints, or indexes associated with the original column.



<a name="loiod868b12b173440f49bf3e9dcd8d32d3f__section_rnm_xbj_41c"/>

## Prerequisites

This data lake Relational Engine task can be completed when connected as follows:

-   Connected to SAP HANA database as a SAP HANA database user.

Requires:

-   You have the REMOTE EXECUTE privilege on the remote source *<hana\_relational\_container\_schema\>*\_SOURCE.

You also require one of the following:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the SAP HANA database REMOTE\_EXECUTE procedure associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loiod868b12b173440f49bf3e9dcd8d32d3f__section_ryy_xbj_41c"/>

## Context

Use the [ALTER TABLE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/alter-table-statement-for-data-lake-relational-engine-sap-hana-db-managed-593f8b1.md) to add keys and constraints to columns.

Use the [CREATE INDEX Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/create-index-statement-for-data-lake-relational-engine-sap-hana-db-managed-afc9ba6.md) to create indexes on columns.

