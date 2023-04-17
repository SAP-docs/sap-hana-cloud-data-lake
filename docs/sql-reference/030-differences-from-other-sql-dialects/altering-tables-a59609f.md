<!-- loioa59609f884f2101580e0fbd7cf321049 -->

# Altering Tables

`ALTER TABLE` has been extended.

In addition to changes for entity and referential integrity, the following types of alterations are allowed:

```
DELETE column
RENAME new-table-name
RENAME old-column TO new-column
```

> ### Tip:  
> After you create a column, you cannot modify the column data type. To change a data type, drop the column and re-create it with the correct data type.

