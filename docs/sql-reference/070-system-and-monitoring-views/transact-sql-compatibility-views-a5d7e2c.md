<!-- loioa5d7e2c784f21015b89aa8dc8650369c -->

# Transact-SQL Compatibility Views

SAP Adaptive Server Enterprise and data lake Relational Engine have different system catalogs, reflecting the different uses for the two products.

In SAP ASE, there is a single master database containing a set of system tables holding information that applies to all databases on the server. Many databases may exist within the master database, and each has additional system tables associated with it.

In data lake Relational Engine, each database exists independently, and contains its own system tables. There is no master database that contains system information on a collection of databases. Each server may run several databases at a time, dynamically loading and unloading each database as needed.

The SAP ASE and data lake Relational Engine system catalogs are different. The SAP ASE system tables and views are owned by the special user `dbo`, and exist partly in the master database, partly in the `sybsecurity` database, and partly in each individual database; the data lake Relational Engine system tables and views are owned by the special user `SYS` and exist separately in each database.

To assist in preparing compatible applications, data lake Relational Engine provides a set of views owned by the special user dbo, which correspond to the SAP ASE system tables and views. Where architectural differences make the contents of a particular SAP ASE table or view meaningless in a data lake Relational Engine context, the view is empty, containing only the column names and data types.

These topics list the SAP ASE system tables and their implementation in the data lake Relational Engine system catalog. The owner of all tables is `dbo` in each DBMS.

