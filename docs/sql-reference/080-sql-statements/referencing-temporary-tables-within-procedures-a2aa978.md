<!-- loioa2aa978c84f210158298c5a888b44e04 -->

# Referencing Temporary Tables Within Procedures

Sharing a temporary table between procedures can cause problems if the table definitions are inconsistent.

For example, you have two procedures `procA` and `procB`, both of which define a temporary table, `temp_table`, and call another procedure called `sharedProc`. Neither `procA` nor `procB` have been called yet, so the temporary table does not yet exist.

Now, if both `procA` and `procB` used the same column names and types but their definitions for `temp_table` differed slightly, the column order would differ.

When you call `procA`, it returns the expected result. However, when you call `procB`, it returns a different result.

This is because when `procA` was called, it created `temp_table`, and then called `sharedProc`. When `sharedProc` was called, the `SELECT` statement inside of it was parsed and validated, and then a parsed representation of the statement is cached so that it can be used again when another `SELECT` statement is executed. The cached version reflects the column ordering from the table definition in `procA`.

Calling `procB` causes `temp_table` to be re-created, but with different column ordering. When `procB` calls `sharedProc`, the database server uses the cached representation of the `SELECT` statement. So, the results differ.

To avoid this from happening, do one of the following:

-   Ensure that temporary tables used in this way are defined consistently
-   Consider using a global temporary table instead

**Related Information**  


[Referencing Temporary Tables Within Procedures](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/5482d9ab347749deb3b5595a7e41bba7.html "Sharing a temporary table between procedures can cause problems if the table definitions are inconsistent.") :arrow_upper_right:

