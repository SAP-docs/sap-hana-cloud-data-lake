<!-- loioa38963a784f210159386f61b1856642e -->

# Identifying and Fixing Invalid Dependent Views for Data Lake Relational Engine

Check for, and correct, any dependent views that become invalid because of changes to their underlying tables.



## Context

Under most circumstances the database server automatically recompiles views to keep them valid if the underlying tables change. However, if your table alteration removes or materially changes something referenced by the view definition, then the dependent view becomes invalid. For example, if you remove a column referenced in the view definition, then the dependent view is no longer valid. Correct the view definition and manually recompile the view.



## Procedure

1.  Run `sa_dependent_views` to get the list of dependent views.

2.  Perform the DDL operation that alters the table. The server automatically disables dependent views, and attempts to recompile them once the DDL is complete.

3.  Check that all the views listed by `sa_dependent_views` are valid. For example, perform a simple test such as `SELECT * FROM myview`.

4.  If a view is invalid, it's likely you need to alter the view definition to resolve the issue. Examine the view definition against the DDL change that you made and make the necessary changes. Run ALTER VIEW RECOMPILE to correct the view definition.

5.  Test the corrected view to make sure it works. For example, perform a simple test such as `SELECT * FROM myview`.




## Results

The `sa_dependent_views` system procedure returns the list of all dependent views for a given table or view.

**Related Information**  


[sa\_dependent\_views System Procedure for Data Lake Relational Engine](../060-stored-procedures/sa-dependent-views-system-procedure-for-data-lake-relational-engine-3be5950.md "Returns the list of all dependent views for a given table or view.")

[ALTER VIEW Statement for Data Lake Relational Engine](alter-view-statement-for-data-lake-relational-engine-a613cd2.md "Replaces a view definition with a modified version.")

