<!-- loio9cff5a55a7d310149ffcfdbdcda0fad8 -->

# sqlany\_get\_rowset\_size\(a\_sqlany\_stmt \*\) Method

Retrieves the size of the row set to be fetched by the sqlany\_fetch\_absolute\(\) and sqlany\_fetch\_next\(\) functions.



```
public sacapi_u32 sqlany_get_rowset_size (a_sqlany_stmt * sqlany_stmt)
```



## Parameters

sqlany\_stmt
:   A statement prepared successfully using sqlany\_prepare\(\).



## Returns

The size of the row set, or 0 if the statement does not return a result set.

**Related Information**  


[sqlany\_set\_rowset\_size\(a\_sqlany\_stmt \*, sacapi\_u32\) Method](sqlany-set-rowset-size-a-sqlany-stmt-sacapi-u32-method-9d0617f.md "Sets the size of the row set to be fetched by the sqlany_fetch_absolute() and sqlany_fetch_next() functions.")

[sqlany\_fetch\_absolute\(a\_sqlany\_stmt \*, sacapi\_i32\) Method](sqlany-fetch-absolute-a-sqlany-stmt-sacapi-i32-method-3bf5955.md "Moves the current row in the result set to the specified row number and then fetches rows of data starting from the current row.")

[sqlany\_fetch\_next\(a\_sqlany\_stmt \*\) Method](sqlany-fetch-next-a-sqlany-stmt-method-3bf59e2.md "Returns the next set of rows from the result set.")

